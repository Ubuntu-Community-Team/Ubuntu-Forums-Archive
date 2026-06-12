---
title: "Local Repository problem"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by rajsarkar on 2006-04-17
Hi,

I Installed Edubuntu 5.10 in an external hdd. Following a post I could make it running.

Then I tried to set up a local repository. I downloaded all files for installing XFCE desktop. Then I followed another posting with detail instruction to set up a local repo. copied the files in a directory on desktop. Added the repo in the source.list file. Made Packages.gz. Then I ran Synaptic. It could read the local repo. 

But when I type ...

sudo apt-get update 
sudo apt-get install xubuntu-desktop

.. it starts downloading the xfce files from the internet. 

I am not sure what could be wrong. Any suggestion??

Thanks in advance.

Raj

---

### Post by sYs^ on 2006-04-17
Did you comment out the internet repos in /etc/apt/sources.list ?

---

### Post by rajsarkar on 2006-04-17
I had installed Automatics previously. So lot of internet repositories are already set (commented out). Am I getting you right?

Raj

---

### Post by sYs^ on 2006-04-17
Sorry but I dont know Automatics :\

But imho if you comment out all of the internet repos then it won't download from the internet, just an idea.

---

