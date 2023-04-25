简体中文🀄 | English🌎

# Contributing to PaddleNLP

We welcome and appreciate your open source contributions to `PaddleNLP`. Before you start submitting your contributions, please sign the [PaddlePaddle Contributor License Agreement](https://cla-assistant.io/PaddlePaddle/PaddleNLP).

The following sections describe our development and contribution process:

## Contribution Ways

We welcome different ways of contributing to `PaddleNLP`, such as:

- Fixing known issues
- Submitting new issues, such as feature requests or bug reports
- Implementing new model structures

If you don't know where to start, please check the `Good First Issue` label in the Issues section. It provides you with a beginner-friendly list of known issues, which can lower the threshold for contribution and help you get started with open-source contributions. Just let us know which issue you want to take on.

## Development Process

PaddleNLP uses the [Git branch model](http://nvie.com/posts/a-successful-git-branching-model/). For common open-source contributions, we have the following contribution process:

#### 1. Fork

As the PaddleNLP development community is constantly evolving, it would be difficult to manage if every contributor directly submits commits to the official repo. Therefore, please submit Pull Requests from your own branch. We recommend that you create your Fork branch through the GitHub ["Fork" button](https://help.github.com/articles/fork-a-repo/).

#### 2. Clone

Please run the following command to clone your branch to your local environment:

```bash
git clone https://github.com/<your-github-account>/PaddleNLP
cd PaddleNLP

   ```
#### 3. Create a Local Development Branch
For daily tasks such as adding new features or fixing errors, create your local development branch before starting development:

   ```bash
   git checkout -b my-cool-feature
   ```

#### 4. Configure the Development Environment
   Before you start coding, you need to set up your development environment. We strongly recommend that you do all development in a virtual environment, such as venv or conda.

After you set up and activate your virtual environment, run the following command:

   ```bash
   make install
   ```

   This sets up all the dependencies of `PaddleNLP`  as well as the  [`pre-commit`]tool (http://pre-commit.com/)。

   If you need to develop the `examples` or `applications` module and load `PaddleNLP`，make sure to install `PaddleNLP`in editable mode（`-e`。
   If `PaddleNLP` ， is already installed in the virtual environment, use `pip uninstall paddlenlp` to remove it and then reinstall it in editable mode with
   `pip install -e .`


#### 5. Development

   When you are developing, make sure that your new code is covered by unit tests. All our unit tests can be found in the `tests` directory. You can modify existing unit tests to cover new functionality or create new tests from scratch. When you are finished with your code, make sure that the relevant unit tests pass. You can run the tests affected by the changes like this:

   ```bash
   pytest tests/<test_to_run>.py
   ```

#### 6. Commit

   We use the [`pre-commit`](http://pre-commit.com/) tool（including[black](https://black.readthedocs.io/en/stable/)、[isort](https:/ /pycqa.github.io/isort/) 和
   [flake8](https://flake8.pycqa.org/en/latest/)）to check the style of the code and documentation in each commit. When you run `git commit`, you will see something like the following:

   ```sql
     ➜  (my-virtual-env) git commit -m "commiting my cool feature"
 black....................................................................Passed
 isort....................................................................Passed
 flake8...................................................................Passed
 check for merge conflicts................................................Passed
 check for broken symlinks............................(no files to check)Skipped
 detect private key.......................................................Passed
 fix end of files.....................................(no files to check)Skipped
 trim trailing whitespace.............................(no files to check)Skipped
 CRLF end-lines checker...............................(no files to check)Skipped
 CRLF end-lines remover...............................(no files to check)Skipped
 No-tabs checker......................................(no files to check)Skipped
 Tabs remover.........................................(no files to check)Skipped
 copyright_checker........................................................Passed

   ```

  But most of the time, things don't go that smoothly. When your code or documentation does not meet the standards, the ，`pre-commit` check will fail.

   ```sql
    ➜  (my-virtual-env) git commit -m "commiting my cool feature"
 black....................................................................Passed
 isort....................................................................Failed
 - hook id: isort
 - files were modified by this hook

 Fixing examples/information_extraction/waybill_ie/run_ernie_crf.py

 flake8...................................................................Passed
 check for merge conflicts................................................Passed
 check for broken symlinks............................(no files to check)Skipped
 detect private key.......................................................Passed
 fix end of files.....................................(no files to check)Skipped
 trim trailing whitespace.............................(no files to check)Skipped
 CRLF end-lines checker...............................(no files to check)Skipped
 CRLF end-lines remover...............................(no files to check)Skipped
 No-tabs checker......................................(no files to check)Skipped
 Tabs remover.........................................(no files to check)Skipped
 copyright_checker........................................................Passed

   ```

   Our tools will automatically fix most style errors, but some errors need to be fixed manually. Luckily, the error messages are generally easy to understand and fix.
   Once you have resolved the errors, you can run git add <files> and git commit again, which will trigger pre-commit again.
   Once the pre-commit check passes, you can push the code.

   [Google][http://google.com/] or [StackOverflow](https://stackoverflow.com/) are good tools to help you understand style errors in the code. If you still can't figure it out, don't worry. You can use `git commit -m "style error" --no-verify` to submit, and we'll be happy to help you after you create a Pull Request.


#### 7. git pull and code conflicts

   Experienced Git users often do `git pull`。from the official Repo, because this way they will notice code conflicts with others early on, and make it easier to resolve them.

   ```bash
   git remote add upstream https://github.com/PaddlePaddle/PaddleNLP
   git pull upstream develop
   ```

#### 8. git push ans submit Pull Request

   You can push your work from your local development branch to your forked branch:

   ```bash
   git push origin my-cool-stuff
   ```

   After `git push`，you can submit a Pull Request to request the [officelrepo](https://github.com/PaddlePaddle/PaddleNLP) and accept your development work. 。Please follow these steps[translates to "these steps"](https://help.github.com/articles/creating-a-pull-request/) to creat a Pull Request。

#### 9. Delete local and remote branches that have been merged

   To keep your local workspace and forked branch clean after your Pull Request has been merged, it is recommended to delete the remaining local branch:

   ```bash
   git push origin my-cool-stuff
   git checkout develop
   git pull upstream develop
   git branch -d my-cool-stuff
   ```

## Code Review

- Once your Pull Request can pass the local test and CI smoothly, you can @ the relevant Reviewers in the Pull Request to remind them to review your Pull Request as soon as possible.

- Please address every comment made by the Reviewer. If you have made changes according to the comment, please reply "done". Otherwise, you can discuss it under the comment.

- If you don't want your Reviewers to be overwhelmed with email notifications，you can use [batch reply](https://help.github.com/articles/reviewing-proposed-changes-in-a-pull-request/)。
