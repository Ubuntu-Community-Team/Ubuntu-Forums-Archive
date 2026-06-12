---
title: "help please error when logging in."
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by terry_gardener on 2007-08-28
when i login i get the following error: 

user's $home/.dmrc file is being ignored. This prevents teh default session and language from being saved. File should be owned by the user and have 644 premissions user's $home folder directory must be ownered by user and not writable by other users. 

please can someone tell how to fix this and stop this message from displaying at login. 

i have included a picture of the premissions on my home folder.

---

### Post by Dr Small on 2007-08-28
Please read this thread:
[http://ubuntuforums.org/showthread.php?t=535555](http://ubuntuforums.org/showthread.php?t=535555)

Dr Small

---

### Post by terry_gardener on 2007-08-28
how do you change the chmod of the home folder

---

### Post by Dr Small on 2007-08-28
Go to the terminal (Applications > Accessories > Terminal) and type the following commands in it.

```
chmod 775 /home/USERNAME 
```
```
chmod 644 /home/USERNAME/.dmrc
```

Dr Small

---

### Post by terry_gardener on 2007-08-28
tried this reboot and still get same error 

any more suggestions.

---

### Post by terry_gardener on 2007-08-28
tried this from other post: [http://ubuntuforums.org/showthread.php?t=371052](http://ubuntuforums.org/showthread.php?t=371052)

sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo

replaced ricardimo with me username and the error has stoped. 

what is the premission set 700 ie what access does this premission allow.

---

### Post by schorsch on 2007-08-28
Please type in a terminal:
```
ls -ld /home/ricardisimo
```
What you should see is something like:
```
drwx------ ...... /home/ricardismo
```
The first 10 characters are the important ones regarding permissions. You have set them to look like that when doing "chmod -R 700 ...."
The first character explains what kind of type the file is (under *nix everything is a file!).
d = directory
c = character device
b = block device
l = link
- = file
Then there are three sets of characters with three characters resp. Minimum is "---" and the maximum is "rwx".
Let's think binary now: You can sort them as
"r   w   x"
"4   2   1"
You get the idea? 4+2+1=7 and so your directory gets those permissions. The other way round a value "0" gives no permissions at all. So the chmod command you used is just a short form of the following command:
```
chmod u+rwx g-rwx o-rwx /home/ricardisimo
```
I did not use  the parameter "-R" as changing permissions and owners recursively change cause any kind of problems so I would not advise to use it! After changing something recursively it will be extremely difficult to get them back. So perhaps if some of the applications you use will throw errors in the future it might be related to permission problems!
Using the short form with the numbers is just a quick way to reach the goal when you are  used to it.
Back to your initial problem:
```
chmod 755 /home/ricardismo
chmod 644 /home/ricardismo/.dmrc
``` should have done the trick, too, without changing anything recursively.
Just a little homework for you:
What permissions do get with 755 and 644? :-)

---

