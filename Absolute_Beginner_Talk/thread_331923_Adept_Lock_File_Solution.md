---
title: "Adept Lock File Solution"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by KarlXII on 2007-01-05
I have noticed that quite a few persons ran into the complicated Adept lock file-problem after trying to install the sun-java5-bin package. Well, here is the solution:

1. Restart your system before doing anything at all.

2. Open up your console and make yourself root [sudo su -].

3. Delete all the lock files [files named 'lock'] in /var/lib/apt/lists/ and in /var/lib/aptitude/ as well as in /var/lib/dpkg/.

4. Now use apt-get via the console [still as root] to determine the java5 problem: apt-get install sun-java5-bin -s. You will see a message that tells you that the package was installed poorly through Adept.

5. Now simply reinstall the sun-java5-bin package on top of the old one: apt-get install sun-java5-bin.

6. Exit the console.

7. Run Adept and you will find out that all your problems are gone.

The thing was that the poorly executed java5 installation via Adept screwed the application up.

Good luck!

---

### Post by Swizzy on 2007-10-22
and how exactly do you delete the lock files as "root"?? i don't quite get it... explain plz?

---

### Post by hencke on 2007-11-19
> **Swizzy said:**
> and how exactly do you delete the lock files as "root"?? i don't quite get it... explain plz?

Swizzy has probably figured it out, but this might help someone:

**Method 1:**
Open a terminal/console. (KMenu->System->Konsole) In the following I will use sudo to gain root privileges separately every time, instead of using "sudo su -" to gain more permanent root privileges.
To remove the lock files type:
```
sudo rm /var/lib/apt/lists/lock
sudo rm /var/lib/aptitude/lock
sudo rm /var/lib/dpkg/lock
```
And possibly (please refer to [http://ubuntuforums.org/showthread.php?t=302629&page=2):](http://ubuntuforums.org/showthread.php?t=302629&page=2):)
```
sudo rm /var/cache/apt/archives/lock
```
FInally
```
sudo dpkg --configure -a
```
should help if your problems aren't only java-related.

**Method 2** (possibly more intuitive to new linux users):
Open a terminal and type:
```
sudo konqueror
```
and then navigate to the folders in question and delete the files named 'lock'. **Remember to close this konqueror window after finished or you might accidentally damage your system.**
FInally
```
sudo dpkg --configure -a
```
should help if your problems aren't only java-related.

By the way: Thanks KarlXII and jordanmthomas from the other thread.
Thanks also to jaybombalous for the link he posted.

---

### Post by jaybombalous on 2007-11-19
ubuntu recommends using 
```

sudo -s
```

to gain root access. that way when the terminal closes so does the root account. :)

```
sudo su
``` 

is dangerous for beginners. If they forget to restart or change back to a user account they could potentially do dangerous stuff they are not aware of by accident.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

