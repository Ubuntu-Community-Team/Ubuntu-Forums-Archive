---
title: "Editing Directories"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-03-30
When trying to copy a file into a folder, it says I do not have the permission to do so.

How can I make it so that I have the permission to edit any folder? Thanks!

---

### Post by 5-HT on 2006-03-30
If the directory is outside of your home directory, you'll need to preface the command with 'sudo' to escalate your privileges so you may  have write permissions.

e.g., sudo cp -i foo bar

Here is a wiki link of relevance: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

HTH

---

### Post by aysiu on 2006-03-30
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

