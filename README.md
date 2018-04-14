# composer-issue

## Reproducing the issue

1. Create new empty directory:
`$ mkdir composer-issue`
2. Change into new directory:
`$ cd composer-issue`
3. Clone the 3 demonstration repositories:
    1. `$ git clone https://github.com/strarsis/composer-issue-package-a`
    2. `$ git clone https://github.com/strarsis/composer-issue-package-c`
    3. `$ git clone https://github.com/strarsis/composer-issue-package-c`
4. Change into demonstration repository B:
`$ cd composer-issue-package-b`
5. Run composer to install its dependencies:
`$ composer update`
It should work.
6. Change into demonstration repository A:
`$ cd ..`
`$ cd composer-issue-package-A`
7. Run composer to install its dependencies:
`$ composer update`
This should fail, composer cannot find sub-dependency `package-c` that `package-b` is using.

Chain:
`package B` -> `package C`: Works correctly
`package A` -> `package B` -> `package C`: Doesn't work correctly, cannot find `package C`.
