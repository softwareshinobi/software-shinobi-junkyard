## URL // https://www.freecodecamp.org/news/how-to-fix-git-always-asking-for-user-credentials/

# How to fix Git always asking for user credentials

Have you ever encountered Git asking you for your username and password every time you try to interact with GitHub even after configuring it? Well, this is a very common problem among users who use the HTTPS clone URL for their repository. In this article, I’ll show you how to fix this.

The https:// clone URLs are available on all public and private repositories. These URLs work everywhere, even if you are behind a firewall or proxy.
clone

When you interact with a remote repository using HTTPS URLs on the command line, you’ll be asked for your GitHub username and password, this sucks right?

Well using an HTTPS remote URL has some advantages: it’s easier to set up than SSH :), and usually works through strict firewalls and proxies. However, it also prompts you to enter your GitHub user credentials every time you pull or push a repository :(.

## You can fix this by configuring Git to store your password for you.

Here’s how:

    Update the URL of origin remote using SSH instead of HTTPS;

git remote set-url origin git@github.com:username/repo.git

or

    Make Git store the username and password and it will never ask for them.

git config --global credential.helper store

    Save the username and password for a session (cache it);

git config --global credential.helper cache

    You can also set a timeout for the above setting

git config --global credential.helper 'cache --timeout=600'

Bingo, you just fixed it, Git will never ask for your credentials again.

## CONCLUSION

However, due to security reasons, it is advisable that you use SSH to interact with GitHub, especially if you work for a company or you’re using a computer that isn’t yours.

Using the SSH protocol, you can connect to GitHub without supplying your username or password every time.

Learn how to connect to GitHub with SSH here.

https://help.github.com/en/articles/connecting-to-github-with-ssh