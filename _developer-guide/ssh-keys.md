---
title: Managing your SSH keys
layout: article
section: Developing Components
order: 0
---

{{site.data.tenant.name}} platform **requires from every developer a unique SSH key to authorise any code deployment into the system**. This is a standardised, industry accepted security feature which is widely used in similar services like GitHub.
![Add your SSH Key](/assets/img/developer-guide/ssh-keys/sshkeys-empty.png "Add your SSH Key")

In this article:

*   [Creating your SSH keys](#creating-your-ssh-keys)
*   [Uploading your SSH Keys](#uploading-your-ssh-keys)

## Creating your SSH keys

GitHub has an informative page on SSH Key generation and what you see here is practically taken from the page [Generating SSH keys](https://help.github.com/articles/generating-ssh-keys/). Before moving forward it would be prudent to check for existing SSH Keys on your computer and if it's necessary to create a new one.

### Check for Existing SSH keys

To see all existing SSH Keys open a terminal and type:
```sh
$ ls -al ~/.ssh
# Lists the files in your .ssh directory, if they exist
...
drwx------   7 username  staff   238 Aug  3 14:08 .
drwxr-xr-x+ 33 username  staff  1122 Jul 24 09:06 ..
-rw-------   1 username  staff  1766 Jun 25 12:29 github_rsa
-rw-r--r--   1 username  staff   403 Jun 25 12:29 github_rsa.pub
-rw-r--r--   1 username  staff  2005 Aug  3 14:11 known_hosts
```

This shows that this user called username has already GitHub created SSH key which is possible to use. We recommend creating a new one for a simplicity and proper record keeping.

### Creating a new SSH key

To create an SSH Key open a terminal and type:
```sh
$ ssh-keygen -t rsa -b 4096
...
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/username/.ssh/id_rsa): [Press enter]
Enter passphrase (empty for no passphrase):  [Type a passphrase]
Enter same passphrase again:  [Type a passphrase]
Your identification has been saved in /Users/username/.ssh/id_rsa.
Your public key has been saved in /Users/username/.ssh/id_rsa.pub.
The key fingerprint is:
01:0f:f4:3b:ca:85:d6:17:a1:7d:f0:68:9d:f0:a2:db username@yourcomputer.local
```
The example above ties your SSH key with your computer.
**Please note:** if you want your SSH key to be connected with your e-mail address then use
```sh
$ ssh-keygen -t rsa -b 4096 -C username@youraddress.com
```
After generating the SSH Key if we check our SSH directory we will get two more entries:
```sh
$ ls -al ~/.ssh
total 40
drwx------   7 username  staff   238 Aug  3 14:08 .
drwxr-xr-x+ 33 username  staff  1122 Jul 24 09:06 ..
-rw-------   1 username  staff  1766 Jun 25 12:29 github_rsa
-rw-r--r--   1 username  staff   403 Jun 25 12:29 github_rsa.pub
-rw-------   1 username  staff  3243 Aug  3 14:08 id_rsa
-rw-r--r--   1 username  staff   755 Aug  3 14:08 id_rsa.pub
-rw-r--r--   1 username  staff  1595 Jul 28 16:14 known_hosts
```
Use the newly generated `id_rsa.pub` key to work with the platform. For the simplicity type:
```sh
$ less ~/.ssh/id_rsa.pub | pbcopy
```
This command copies the newly created SSH Key into your clipboard, so that you can paste somewhere else.

## Uploading your SSH keys

To add a newly generated SSH Keys navigate to `Settings > SSH Key` section:
![Adding the new SSH Key](/assets/img/developer-guide/ssh-keys/sshkeys-addnew-copied.png "Adding the new SSH Key")
The final result would look like this:
![Your SSH Keys](/assets/img/developer-guide/ssh-keys/sshkeys-key.png "Your SSH Keys")
You can add more SSH keys or delete the current one on this interface.
