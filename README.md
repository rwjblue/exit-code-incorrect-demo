# exit-code-incorrect-demo

When running `ember try:one some-scenario` the exit code will be `0` even if there are test failures. I noticed this while digging into an issue in ember-engines (which uses ember-cli/ember-cli#master to make sure it still works properly against master).

Steps to reproduce:

```
ember new exit-code-incorrect-demo
cd exit-code-incorrect-demo
npm install github:ember-cli/ember-cli # to get master installed

# emits "fail" properly
ember test && echo 'pass' || echo 'fail'

# this should emit "fail" but does not
ember try:one default && echo 'pass' || echo 'fail'
```
