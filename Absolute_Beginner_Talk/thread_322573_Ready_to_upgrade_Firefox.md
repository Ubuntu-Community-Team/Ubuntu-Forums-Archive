---
title: "Ready to upgrade Firefox"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by Paul_world10 on 2006-12-20
Hello,   I am running Dapper Drake 6.06 on my PC.  I have noticed that it comes along with version 1.5.0.8 and I am wondering if I should upgrade my version. What would be the best fool proof way for me to go about upgrading my firefox version if this is a good idea?   Thank you

---

### Post by slackjack on 2006-12-20
You could try: apt-get install firefox. If there is an updated version available, it should upgrade.

---

### Post by Bachstelze on 2006-12-20
Some people habe problems with Edgy but as far as my ecperience go, it's really solid so if I were you, I'd go for it. If you want to stay with Dapper though, it's pretty easy to install the build from Mozilla.com, just search the Wiki, there's a page about it.

---

### Post by moredhel on 2006-12-20
I am not currently on gnome (xfce atm), but is there not somewhere in the menu a 'update manager?', does that not have it in?

Sorry I don't know off hand if it does - I am on edgy...

---

### Post by ThrobbingBrain66 on 2006-12-20
> **Paul_world10 said:**
> Hello,   I am running Dapper Drake 6.06 on my PC.  I have noticed that it comes along with version 1.5.0.8 and I am wondering if I should upgrade my version. What would be the best fool proof way for me to go about upgrading my firefox version if this is a good idea?   Thank you

Follow this howto step-by-step, and you'll have Fx 2.0 with a quickness.
[https://help.ubuntu.com/community/FirefoxNewVersion?highlight=%28newversion%29](https://help.ubuntu.com/community/FirefoxNewVersion?highlight=%28newversion%29)

---

### Post by manny0 on 2006-12-20
i just replaced the folder with the new folder... is that not the way i should of upgraded lmao,, it seems to work fine so far though :/

---

### Post by aysiu on 2006-12-20
This script will install Firefox 2.0 for you:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by louieb on 2006-12-20
> **aysiu said:**
> This script will install Firefox 2.0 for you:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)
I have Dapper running on 3 PC's. Using aysiu's guide, Firefox 2 installed and works without a problem on all three,

---

### Post by alienexplorers on 2006-12-20
Follow aysiu's script it runs like a charm and got FF 2.0 running on my old system.

---

### Post by matchstich on 2006-12-20
how do we get the update for firefox. supposed to be 2 of them .  when i check update, it grey's out
thanks

---

### Post by Paul_world10 on 2006-12-21
Hello again ,   I have tried now running the Psyconauts script which downlods the Firefox 2.0 or whatnot.   Everything seems to go great untill the ending when we validate the  signature. 


IF i could please ask for more advise I would appreciate it.

I am running {Dapper Drake 6.06} 

the script was    4.
      cd ~/Desktop
      chmod +x installnewfirefox.sh
      ./installnewfirefox.sh



Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: requesting key 1AF32821 from hkp server subkeys.pgp.net
gpg: key 0E3606D9: "Mozilla Software Releases <releases@mozilla.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Thu 14 Dec 2006 05:41:40 PM CST using DSA key ID 0E3606D9
gpg: BAD signature from "Mozilla Software Releases <releases@mozilla.org>"
Previous command did not complete successfully. Exiting.
paul@desktopbox:~/Desktop$

If I may ask did this go alright?   please help me

---

### Post by Bachstelze on 2006-12-21
Maybe you'll be more lucky with this :

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by ThrobbingBrain66 on 2006-12-21
> **matchstich said:**
> how do we get the update for firefox. supposed to be 2 of them .  when i check update, it grey's out
thanks

if you're using the Firefox build that came with Ubuntu, you will be prompted to update in a day or two when the updates are put into the repos.

If you're using the mozilla build, then you have to open a terminal and type
```
gksu firefox
```
then go to help > check for updates and it will update.
When it asks if you want to restart now or later, choose later.  then close the browser and open it again using the command above.  This will complete the update.  

*If you choose to restart the browser right away, it will not open as root and thus not complete the update

---

### Post by aysiu on 2006-12-21
With the newest version of the script, I believe you're allowed to skip the key verification process if it's unsuccessful.

---

