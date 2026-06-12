---
title: "How to get root privilleges?"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by menchi on 2006-09-12
Sorry to bother you i think it's a stupid question but how can I get root privilleges because the root user made it's own password when I installed ubuntu..I need the account to install Skype ](*,)

---

### Post by blakesmith on 2006-09-12
Use **sudo** before the command and type in your username's password... root has a random password in Ubuntu for security purposes.

---

### Post by LotsOfPhil on 2006-09-12
Preface a command with 'sudo' to run it as root. You will be prompted for a password. Enter your password (not the root one).

for example, instead of: 
apt-get install skype

type:
sudo apt-get install skype

---

### Post by Sef on 2006-09-12
First, it is not a stupid question.

Second, you don't need root to install skype.

Third, to install more software, you need to add universe and multiverse to your repositories.  [(Adding Repositories)]("https://help.ubuntu.com/community/Repositories/Ubuntu")

Fourth, Here is how to install software after adding the repositories.  [(Install Anything)]("http://monkeyblog.org/ubuntu/installing/")

Fifth, this explains why sudo is better than root.  [(Root/Sudo)]("https://help.ubuntu.com/community/RootSudo")

---

