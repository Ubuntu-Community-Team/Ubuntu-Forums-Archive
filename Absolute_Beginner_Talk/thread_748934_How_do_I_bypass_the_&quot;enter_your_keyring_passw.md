---
title: "How do I bypass the &quot;enter your keyring password&quot; for wireless internet?"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by diablo75 on 2008-04-07
I just installed a fresh copy of 8.04.  When I start my PC, it asks me to type in a keyring password for the nm-applet.  How do I make this automatically happen so I don't have to rely on this for my Internet connection to auto connect after login?

---

### Post by Inxsible on 2008-04-07
you can disable it by ```
sudo aptitude install libpam-keyring
```

after installation ```
gksudo gedit /etc/pam.d/gdm
```
and add the following line at the end```
@include common-pamkeyring
``` Then restart x by hitting Ctrl + Alt + Backspace

---

### Post by diablo75 on 2008-04-07
The reason I'm doing this is so if I ever need to restart my PC remotely, I don't have to worry about asking someone who's at my house to type in my keyring password.

Anyway, I did what you suggested, and restarted my PC... and I am not actually in front of it at the moment, but I restarted it and can't connect to it now.  So I'm just assuming it didn't work.  When I get home, I'll let you know what I discover there.

---

### Post by Inxsible on 2008-04-07
Let us know if it works !!!

---

### Post by Inxsible on 2008-04-07
Off topic, but if you want to access your computer remotely, what are you using?

I am assuming its graphical, since the keyring manager is asking for the password. Do you VNC or use NXServer ?

---

### Post by diablo75 on 2008-04-08
It appears to have done nothing (see attachment).

What else can I try?

---

### Post by bookman79 on 2008-04-08
Thank you so much for this information! I have been using Ubuntu
for a week and like it so much, but the need to login to the wireless
every time I rebooted was such a pain. I am trying to learn on my own
as much as I can but it's nice to know resources like this are here.

---

### Post by Inxsible on 2008-04-09
> **diablo75 said:**
> It appears to have done nothing (see attachment).

What else can I try?Are you sure you added the appropriate line to the appropriate file as mentioned?

---

### Post by bookman79 on 2008-04-09
I tried this and initially thought it worked but then five minutes in I lost my internet
connection and it asked for the password again. I would normally only consider this
outcome a disappointment yet now even with the password entered it refuses to 
connect online. I had to jump over to Vista to seek out help, and thus am able to 
connect, just not through Ubuntu. I have only run Linux for a week and so I copy
and pasted your command lines as I am not proficient. Is there a way to undo what
I have done? I would much rather type the password than have to do a re-install
to start anew. Any help on either where I went wrong or solutions for the problem.
Thanks a lot and this forum has been a great resource for me.

---

### Post by martyway on 2008-04-09
I'm not sure this will help. However I have my wireless set for "manual configure" and I do not have to log in to the key ring when I boot the system. Click on the signal strength icon and choose manual configuration. You may have to set a few parameters, but if you have the wireless working it shouldn't be a problem

Marty

---

### Post by carney1979 on 2008-04-09
> **Inxsible said:**
> you can disable it by ```
sudo aptitude install libpam-keyring
```after installation ```
gksudo gedit /etc/pam.d/gdm
```and add the following line at the end```
@include common-pamkeyring
``` Then restart x by hitting Ctrl + Alt + Backspace

I get an authentication error with GDM when I do this and I cannot login. 

When I added the line to the end of the file, I added no <return> because there appeared to be none at the end of the original file.

Was this a mistake?

David

---

### Post by stchman on 2008-04-09
You must make sure that the keyring password matches your login password.

---

### Post by Inxsible on 2008-04-09
> **carney1979 said:**
> I get an authentication error with GDM when I do this and I cannot login. 

When I added the line to the end of the file, I added no <return> because there appeared to be none at the end of the original file.

Was this a mistake?

DavidOk In your case (this has happened to a few people) you need to login to recovery mode and then type```
sudo nano /etc/pam.d/gdm
``` Remove the line that you had added i.e.```
@include common-pamkeyring
```Save the file and exit. Then do this```
sudo nano /etc/pam.d/login
``` Add the line that you removed from gdm to this new file. Save and restart your machine.

---

### Post by diablo75 on 2008-04-09
> **Inxsible said:**
> Are you sure you added the appropriate line to the appropriate file as mentioned?

Here's a copy of my file:

```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password
@include common-pamkeyring
```

---

### Post by Inxsible on 2008-04-09
> **diablo75 said:**
> Here's a copy of my file:

```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password
@include common-pamkeyring
```
and you also installed the libpam-keyring package right ? I remember you did it thru VNC or something. Would you mind installing the package again on the same machine ie locally,  and then following all instructions. I know this works, so I am surprised it doesn't for you. Sorry.

Or could you try what I suggested to carney1979 ? Let me know if that works for you.

---

### Post by diablo75 on 2008-04-09
> **Inxsible said:**
> Ok In your case (this has happened to a few people) you need to login to recovery mode and then type```
sudo nano /etc/pam.d/gdm
``` Remove the line that you had added i.e.```
@include common-pamkeyring
```Save the file and exit. Then do this```
sudo nano /etc/pam.d/login
``` Add the line that you removed from gdm to this new file. Save and restart your machine.

I'll try this....

---

### Post by carney1979 on 2008-04-09
> **stchman said:**
> You must make sure that the keyring password matches your login password.

Is there a way to change your keyring password? I did change my login password, that's when my problems with having to enter my old password to get my wireless working appeared.

As security conscience as Ubuntu and Linux are it seems really numb that you can't change your login password with out being able to change your keyring password to match, or even to just be able to change your keyring password to anything you want.

David

---

### Post by diablo75 on 2008-04-09
> **Inxsible said:**
> and you also installed the libpam-keyring package right ? I remember you did it thru VNC or something. Would you mind installing the package again on the same machine ie locally,  and then following all instructions. I know this works, so I am surprised it doesn't for you. Sorry.

Or could you try what I suggested to carney1979 ? Let me know if that works for you.

I use VNC....

Here's what happens when I go to install that package:

```
zeke@zeke-desktop:~$ sudo apt-get install libpam-keyring
[sudo] password for zeke: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libpam-gnome-keyring instead of libpam-keyring
libpam-gnome-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
zeke@zeke-desktop:~$ 

```

I just finished trying to set up the connection manually (as suggested at the bottom of the first page of this thread) and for some reason it doesn't connect at all.  ifconfig show no IP address or ESSID listed as it's suppose....  Maybe I needed to restart the PC after entering the config...I'm going to try that, then the other stuff involving recovery mode... I'll be back in a little while with more results...

---

### Post by Inxsible on 2008-04-09
> **carney1979 said:**
> Is there a way to change your keyring password? I did change my login password, that's when my problems with having to enter my old password to get my wireless working appeared.

As security conscience as Ubuntu and Linux are it seems really numb that you can't change your login password with out being able to change your keyring password to match, or even to just be able to change your keyring password to anything you want.

DavidYou can simply delete the keyring from the keyring manager and then having the @include common-pamkeyring line in your login file makes sure that the keyring manager never even asks you to create a password. Then you dont have to worry about changing keyring passwords at all.


BTW, were you able to get rid of the authentication error and login to your Ubuntu?

---

### Post by diablo75 on 2008-04-09
> **Inxsible said:**
> You can simply delete the keyring from the keyring manager and then having the @include common-pamkeyring line in your login file makes sure that the keyring manager never even asks you to create a password. Then you dont have to worry about changing keyring passwords at all.


BTW, were you able to get rid of the authentication error and login to your Ubuntu?

You caught me just before I was going to restart and follow the instructions that are intended to be run in recovery mode....  So before I restart, here's a screenshot of my keyring manager.  Are you saying, with the line that I have in my gdm file, I can just delete the "login" keyring show in the attached screenshot?

---

### Post by carney1979 on 2008-04-09
> **Inxsible said:**
> 

BTW, were you able to get rid of the authentication error and login to your Ubuntu?

After applying your latest fix, I was able to login using GDM, no problem. But I still got the error, had to enter my old password to get my wireless to work. Plus I could not login to a tty (not terminal) after hitting ctrl-alt-f1.

So I removed the line from from the login file.

I've followed the instructions completely, as outlined. I've been using Linux since the mid-1990's, the FVWM days. I know how to follow directions.

It is a good idea to change passwords from time to time. I do like to change my password. 

I would prefer NOT to "bypass" my keyring password. That's is why I asked if there was a way to change it. 

Is there a way to change it, not bypass it?

David

---

### Post by Inxsible on 2008-04-09
> **carney1979 said:**
> After applying your latest fix, I was able to login using GDM, no problem. But I still got the error, had to enter my old password to get my wireless to work. Plus I could not login to a tty (not terminal) after hitting ctrl-alt-f1.

So I removed the line from from the login file.

I've followed the instructions completely, as outlined. I've been using Linux since the mid-1990's, the FVWM days. I know how to follow directions.

It is a good idea to change passwords from time to time. I do like to change my password. 

I would prefer NOT to "bypass" my keyring password. That's is why I asked if there was a way to change it. 

Is there a way to change it, not bypass it?

DavidNot that I know of. You would have to delete the keyring and then when you login, it will ask you to setup a new key and you can set up a new password.

---

### Post by carney1979 on 2008-04-09
OK, I'm all fixed here.

I removed the /home/.gnome2/keyrings/login.keyring file. Note that .gnome2 is a hidden folder, you must use ctrl-h in Nautilus to see it unless you have Nautilus set to always show hidden files and folders.

I rebooted, then logged into Gnome. I was asked to enter my wireless password again (using a secure router with  wpa encryption here, my password for it is 22 random characters with mixed numerals/letters and mixed upper/lower case).

After the wireless connected to the router, I again rebooted and then logged into Gnome again. Gnome started normally and the wireless started normally and I was not asked for a second password. FINALLY FIXED HERE!!

Thanks all!

David

---

### Post by diablo75 on 2008-04-09
I've got a headache from the beer last night, so I'm going to hold off on this experiment until later.  I just got back from walking the dogs for an hour and it was much more satisfying for some reason...

I'll be back.. :)

---

### Post by stchman on 2008-04-09
> **carney1979 said:**
> Is there a way to change your keyring password? I did change my login password, that's when my problems with having to enter my old password to get my wireless working appeared.

As security conscience as Ubuntu and Linux are it seems really numb that you can't change your login password with out being able to change your keyring password to match, or even to just be able to change your keyring password to anything you want.

David

Go to the Keyring Manager via System--->Administration--->Keyring Manager.  You will need to delete your keyring.  After that connect to your secure wireless connection and make the new keyring password the same as your login password.

---

### Post by Tews on 2008-04-09
Keep in mind also that if you have set your account to "auto login" that the keyring manager will ask for your password..  I never found the reasoning for this but as soon as I disabled that option, I was no longer required to enter my password to connect to the net ... go figure ...

---

### Post by jakommo on 2008-04-13
> **Tews said:**
> Keep in mind also that if you have set your account to "auto login" that the keyring manager will ask for your password..  I never found the reasoning for this but as soon as I disabled that option, I was no longer required to enter my password to connect to the net ... go figure ...

Hi,

does someone know how to disable or bypass this?
I have my laptop setup with a entire encrypted system and I use autologin on gdm but then I have to enter the password for the keyring to connect to my wifi.
I have to enter my luks password at boot up so its only me who can boot into this system and after that I dont want to login again on gdm or the keyring-manager.

any ideas?

regards

jakommo

---

### Post by Cannaregio on 2008-04-13
Take the following *cum grano salis*, since the keyring bazaar only happened to me on two laptops out of a total of 4 boxes connected via router chez moi. Two other boxes worked without problem all the time. Since all 4 boxes are completely different (processors, wifi cards, even ubuntu versions) it's difficult to say why those two and not the other two.

Went browsing and found a lot of recent messages about this keyring password crap, which seems to confirm that something went havoc during a recent update.

Tried all possible tweakings (disinstalled network-manager and substituted with [COLOR="Blue"]wifi-radar[/COLOR] and/or [COLOR="#0000ff"]wicd[/COLOR], killed [COLOR="#0000ff"].gnome2/keyrings/etc[/COLOR]...) to no effect.

Tried various live/CDs: ubuntu 7.10, Ubuntu 8.4 beta, Sabayon... to no avail. Still asking for the keyring password on these live sessions. And no connection on wep protected routers (but they worked on unprotected ones).

Tried both gnome and kde versions... to no avail.

I was slowly getting desperate.

And now the happy ending:

both "faulty" laptops suddendly worked again (with [COLOR="#0000ff"]wicd[/COLOR]) AFTER RESETTING MY ROUTER.  No keyring questions anymore.

What I have learned:
1) This keyring manager app is the pure annoying crap. Hope the responsible developers will be pancaked by a truck.
2) Something (dunnow what) MUST have wreaked some havoc in network manager or in keyring manager with the recent updates. Else I wouldn't have had TWO boxes suddendly malfunctioning.
3) It is good to have many neighbours with unprotected and wep protected access.

Well, that was it, for what it is worth. All my boxes now work well.

---

### Post by JBA2337 on 2008-04-15
I have tried this method several times, and it does not work for me. I still have to enter my keyring password every time I boot my computer. 

Before I started, I set both my keyring password and my login password to the same set of characters.

Right after I installed libpam-keyring, and added "@include common-pamkeyring" to the /etc/pam.d/gdm file, I rebooted my computer and an error message came up that said "Authentication Failed". The computer would not boot up at all. So I shut completely down, started up again, and my computer started normally, except that I still have to put in a keyring password.

I have a Toshiba laptop model A105, and the only operating system on it is Ubuntu 7.10.
Any other ideas how I can eliminate entering the keyring password?

JBA2337

---

### Post by Inxsible on 2008-04-15
> **JBA2337 said:**
> I have tried this method several times, and it does not work for me. I still have to enter my keyring password every time I boot my computer. 

Before I started, I set both my keyring password and my login password to the same set of characters.

Right after I installed libpam-keyring, and added "@include common-pamkeyring" to the /etc/pam.d/gdm file, I rebooted my computer and an error message came up that said "Authentication Failed". The computer would not boot up at all. So I shut completely down, started up again, and my computer started normally, except that I still have to put in a keyring password.

I have a Toshiba laptop model A105, and the only operating system on it is Ubuntu 7.10.
Any other ideas how I can eliminate entering the keyring password?

JBA2337Did you try to remove the line from gdm file and put it in the login file like I mentioned in post  #13

---

### Post by JBA2337 on 2008-04-16
Yes, I removed the line from the gdm file and put it in the login file. I followed your instructions exactly, as in your post #13. But I still have to enter a keyring password every time I boot up my computer.

I noticed two things that might be important in analyzing my problem.

(1) When I installed  libpam-keyring, it appears that nothing was actually installed. Here is the exact text from my Terminal session:

:~$  sudo aptitude install libpam-keyring
[sudo] password for jim:__
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done  

(2) The second thing I noticed is that when I open the Keyring Manager, and click on VIEW KEYRINGS, there are two keyrings listed, named login and default. The word  "login" is in boldface type.

Both my login password and my keyring password are the same.

Any other suggestions?

JBA2337

:confused:

---

