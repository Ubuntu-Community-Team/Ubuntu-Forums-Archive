---
title: "[SOLVED] error, please help"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by k33bz on 2007-05-10
im getting this error, 

ps i decided to fix the problem rather than use a clean install, gets me more familiar with it anyhow.  but any way im tryin re update everything again, till i got everything fixed, to fill peeps in, i recently upgarded from edgy to fiesty, and had several problems. Was advised to back-up files, and do a clean install, and personally i rather get my hands dirty. any way this is the error message i am getting.

E: I wasn't able to locate a file for the sun-java6-bin package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

---

### Post by bobplano on 2007-05-11
are you using synaptic or the terminal? the first error might be a sources error so you need to add some repos (not sure which ones though). the second one just means that you aren't using sudo or if your using synaptic then it is broken

---

### Post by k33bz on 2007-05-11
im doin all this inside the terminal, and i better go check to my repositories to see if my update changed that too.

as far as the second one i am using sudo, :( so waht would that mean if i am using sudo in the terminal and i get that error

---

### Post by k33bz on 2007-05-11
here is the whole thing, minus my computers name of course :)

```
k33bz@xxxxxxx:~$ sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  sun-java6-bin 
The following NEW packages will be installed:
  sun-java6-fonts sun-java6-jre sun-java6-plugin 
0 packages upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 14.7MB will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java6-bin package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
k33bz@xxxxxxx:~$ 

```

---

### Post by bobplano on 2007-05-11
are you on the account you entered when you installed ubuntu? otherwise you might not have access to sudo. does it ask you for your password? i don't see it there. if its not there then that means you edited your files or you already used sudo, implying that it works

---

### Post by k33bz on 2007-05-11
ya, i only have one account, well other than root. but i only made one account

and ya it had already prompted for my password, but i made a lil mistake when i first put it the command, i forgot to put install after aptitude, :(
a fresh look at it, just exited out of terminal and started a new session.

k33bz@xxxxxxxxxxxx:~$ sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  sun-java6-bin 
The following NEW packages will be installed:
  sun-java6-fonts sun-java6-jre sun-java6-plugin 
0 packages upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 14.7MB will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java6-bin package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
k33bz@xxxxxxxxxx:~$

---

### Post by Nythain on 2007-05-11
make sure your /etc/apt/sources.list file looks ok as far as repos being enabled and set to feisty
then try:
sudo dpkg --configure -a
sudo aptitude clean
sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
might help, might not... also make sure you dont have synaptic open while trying to run any dpkg or aptitude commands in terminal

---

### Post by k33bz on 2007-05-11
> **Nythain said:**
> make sure your /etc/apt/sources.list file looks ok as far as repos being enabled and set to feisty
then try:
sudo dpkg --configure -a
sudo aptitude clean
sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
might help, might not... also make sure you dont have synaptic open while trying to run any dpkg or aptitude commands in terminal

well i didnt have that same problem that i was having with those errors, so thanx for that. but not sure if it actually worked, i went through the whole licensing prompt and everything, and it loaded in the terminal, last few things that it posted out is got me wondering if it worked or not.

Setting up sun-java6-fonts (6-00-2ubuntu2) ...
No CIDSupplement specified for Gulim-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Headline-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.

Setting up sun-java6-plugin (6-00-2ubuntu2) ...

k33bz@xxxxxxxx:~$

---

