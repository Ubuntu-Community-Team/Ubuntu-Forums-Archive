---
title: "OpenOffice the user interface language cannot be determined"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-22
After installing Gutsy, OpenOffice would not start.  I read a post that recommended removing and then reinstalling OpenOffice.  Well, I did that and now I get the message:

  The user interface language cannot be determined

Carl

---

### Post by realvz on 2007-10-22
when you uninstalled it...did you purge

if not try this 

sudo apt-get remove (i dont know the package name for openoffice)
and then do
sudo apt-get clean
sudo apt-get remove
sudo apt-get autoremove
and the install OO again

---

### Post by cwmoser on 2007-10-22
Till get the interface language message.

I used the package name OpenOffice.org as in sudo apt-get remove OpenOffice.org.

After uninstalling and then reinstalling, I still get the same error message.

Carl

---

### Post by realvz on 2007-10-22
did you try --purge??

sudo apt-get remove --purge OpenOffice.org.

---

### Post by cwmoser on 2007-10-22
I tried this:

sudo apt-get clean openoffice.org
sudo apt-get remove openoffice.org
sudo apt-get autoremove openoffice.org
sudo apt-get remove --purge openoffice.org

sudo apt-get install openoffice.org


and this:
$ env | grep LANG
LANG=en_US.UTF-8
GDM_LANG=en_US.UTF-8

$

Still get the same "The user interface language cannot be determined" error.

Carl

---

### Post by realvz on 2007-10-22
what is your language set to in ubuntu...

---

### Post by cwmoser on 2007-10-22
> **realvz said:**
> what is your language set to in ubuntu...

How do you discern that?  
I am in the USA - it should be English.

Carl

---

### Post by achintya on 2008-02-09
For me, openoffice used to give the error "the user interface language cannot be determined".

I noticed the following:
#1. Openoffice did not give error when I launch openoffice in superuser (root) mode. However, with regular user login, I got the above error.

#2. The ownership and group-id of "/home/<user>/.openoffice.org2/" directory and all directories/files underneath it is set to 'root'. This is likely to happen as we all do 'apt-get install' in superuser/root mode when installing openoffice.org.

As a solution I changed the ownership ".openoffice.org2" in HOME dir:
============================================
1. get into superuser/root mode:
sudo -i

2. change working-dir to HOME of your regular user-login
cd /home/<user_name>

3. See what your user-id (uid) and group-id (gid) are in the directory listing. Take a note of the uid and gid corresponding to "." entry in directory listing.
ls -al | more 

4. check if the uid and gid of ".openoffice.org2" dir show anything different from uid and gid (which you noted in step 3). For openoffice to work without above error, the uid and gid should NOT be  "root" and "root".
ls -al | grep openoffice.org

5. Set the uid and gid of ".openoffice.org2" and of all files/directories  underneath it recursively to your regular uid and gid (which you noted in step 3).
chown -R <user_name>:<user_group> .openoffice.org2 


Thanks.

---

### Post by Hagar Delest on 2008-02-10
As a workaround, you can try to install the official version of OOo : [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by ivanoz on 2008-05-01
Hey I had the same problem that ACHINTIA describes, but with Hardy, and this is how I solved:
```

$ cd ~
$ sudo chown --reference=. -R .openoffice.org2
$ sudo chmod -R 0755 .openoffice.org2 

```

It worked just fine.

Cheers

---

### Post by lordadi on 2008-06-16
Hi guys,

In Hardy I also used to get the same error. Following this link I got it working:[http://katana.oooninja.com/w/openoffice.org/troubleshooting]("http://katana.oooninja.com/w/openoffice.org/troubleshooting").
[LIST=1]
[*]Close all OpenOffice windows
[*]```
mv ~/.openoffice.org2 ~/.openoffice.org2.backup
```
[*]Restart OpenOffice
[/LIST]

Then all should be well.

This worked for me.

LordAdi

As I understand this, the command "mv ~/.openoffice.org2 ~/.openoffice.org2.backup" causes your user configs etc to be renamed and forces OpenOffice to start with defaults.

---

### Post by calc on 2008-06-19
I think I know what might have been causing the ownership of the ~/.openoffice.org2 to be getting set to root and if so it should be fixed now with hardy-updates and in intrepid. But for users where it is already screwed up you will have to do what was previously noted about resetting it back to the proper uid/gid, etc.

---

### Post by The Populist on 2008-06-22
Ok, I am having the same problem. 

After auto-installing update manager that included many Openoffice updates, the program is flaky and wont load from my taskbar. Although I can still access my files through documents, (thank God).

So which terminal command do I use, the one from post #10 or #11?

...

---

### Post by Hagar Delest on 2008-06-22
First try the #11 and if no change, go with the #10.

---

