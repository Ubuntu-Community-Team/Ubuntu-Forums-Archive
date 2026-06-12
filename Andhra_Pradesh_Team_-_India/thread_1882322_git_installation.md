---
title: "git installation"
date: 2011-11-17
forum: Andhra Pradesh Team - India
---

### Post by atcajith on 2011-11-17
hello every one,

I am new to linux(ubuntu). I want to install a version control- git on my ubuntu server and allow access to my team mates from both ubuntu and windows.

[FONT=Arial]I have followed the instructions mentioned [here]("https://help.ubuntu.com/community/Git?action=fullsearch&context=180&value=linkto%3A%22Git%22").( [https://help.ubuntu.com/community/Git](https://help.ubuntu.com/community/Git)).

but after I distributed the public key of my local system(using ubuntu). I was able to initialise the  gitosis using

[/FONT][FONT=Arial]sudo -H -u gitosis gitosis-init < initialKeyFileName.

But the next step which I performed on the client failed reporting "git is not installed".
and asking me to install it using "apt-get install git-core"

Is it so that I have to install git on my local system also.

please comply if I am ignorant of any basic information.

I request to please respond.

regards,
atcajith
[/FONT]

---

### Post by surfer on 2011-11-17
yes, you have to install git on every client you want to be able to check things out.

---

### Post by atcajith on 2011-11-17
Thank you surfer.

But now after the installation of git on my client, I tried to clone again, but it prompted for password for "gitosis@yourserver.com" but I have no password for it.

Is it better to remove every thing and start from the first step.

But then to remove how do I delete the user "git" created at /home. Its not found in the list of users. and the folder does not get deleted.

I have been trying to install git for the past two days. its become an embarrassment now.

please help me.

---

### Post by atcajith on 2011-11-17
oh. sorry every one out there

I made a mistake of giving the wrong path for cloning, I had to give a more precised path.

Now its cloned
after creating a new project and if I try to create a project folder in my local host and push it to the server it gives me the following error


shyam@ubuntu:~/testPro$ git remote add origin [email]git@172.25.148.3:testPro.git[/email]
shyam@ubuntu:~/testPro$ git push origin master
git@172.25.148.3's password: i entered my password
fatal: 'testPro.git' does not appear to be a git repository
fatal: The remote end hung up unexpectedly


can any one please help.

regards,
Ajith

---

