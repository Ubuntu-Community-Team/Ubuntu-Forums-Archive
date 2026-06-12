---
title: "Another Dapper question"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-05-08
Hi !

Im using Ubuntu Breezy 5.10 and are really thinking of upgrading to Dapper.

I have a few concerns though. 

1) Is it possible to apt-get from Breezy to Dapper? If yes, will I loose my current settings (home folder, installed aps ect..)?

2) Will it be possible to apt-get remove back to breezy? Again without loosing current settings?

3) Is it limited which programs I can use and install on Dapper, or is it the same as on Breezy? 

Thats my 3 primary concerns/questions about upgrading. I really want to try Dapper (with Xgl :P ) and other stuff, but are not sure if this is possible without  a reinstall.

Thanks a lot for reading.

---

### Post by Sef on 2006-05-08
> 1) Is it possible to apt-get from Breezy to Dapper? If yes, will I loose my current settings (home folder, installed aps ect..)?

Yes.  either by a clean install (using a cd to install Dapper) or by a dist-upgrade

Open the terminal

sudo apt-get update

sudo apt-get dist-upgrade

Note: apps will be upgraded or changed, if a different one is installed on Dapper.  Home settings should not be changed, although it is possible to lose them on occassion. **Back up** your data before going to Dapper.

> 2) Will it be possible to apt-get remove back to breezy? Again without loosing current settings?

Not sure. Would have to check out.

> 3) Is it limited which programs I can use and install on Dapper, or is it the same as on Breezy? 

It will affect all the programs which are installed and either upgraded or new or no longer on Dapper.

---

### Post by aktiwers on 2006-05-08
Thanks for your reply!

after the sudo apt-get upgrade, when I do the sudo apt-get dist-upgrade I get the following message:
> aktiwers@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
aktiwers@ubuntu:~$
 
What is wrong here? Maybe I do remember I have done this command before?
Does this mean that I am already using Dapper ? :confused::mrgreen::-k

---

### Post by confused57 on 2006-05-08
I've been looking into dist-upgrading and the various howto's, someone in another thread gave a link to do it this way(looks pretty simple?):

[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)


Sounds a little more automatic...

---

### Post by halfvolle melk on 2006-05-08
My guess is you didn't edit your sources.list. My advise is wait 2 more weeks until Dapper is stable.

---

### Post by catlett on 2006-05-08
Dapper does not come out until June 1st. So a apt-get dist-upgrade right now upgrades to Breezy. After June 1st a dist-upgrade will be a Dapper upgrade. The  dist-upgrade, upgrades you to the current stable version not the testing version or unstable version.

---

### Post by aktiwers on 2006-05-08
Thanks for your replys. 

[quote=confused57]I've been looking into dist-upgrading and the various howto's, someone in another thread gave a link to do it this way(looks pretty simple?):

[https://wiki.ubuntu.com/DapperUpgrades]("https://wiki.ubuntu.com/DapperUpgrades")


Sounds a little more automatic...[/quote] 

After doing what it says on this Wiki, the upgrade to dapper shows up, and I click upgrade.

Then it starts downloading, but on the last one I can only download 61 out of 62 packages? Then it stops totally, until it tells me my connections is not working?

Any ideas?


EDIT:

This keeps happening. Here is a screenshot:

---

### Post by Sef on 2006-05-08
> Dapper does not come out until June 1st. So a apt-get dist-upgrade right now upgrades to Breezy. After June 1st a dist-upgrade will be a Dapper upgrade. The dist-upgrade, upgrades you to the current stable version not the testing version or unstable version.

Not true if you change your sources to Dapper.  After 1 June first you will not have to change your sources list as you point out.  (This is not directed toward you, Catlett, but to those absolute beginners.)

> Then it starts downloading, but on the last one I can only download 61 out of 62 packages? Then it stops totally, until it tells me my connections is not working?

Any ideas?

Wine and theli are the problems.  If you have them on backports, you could unistall them and see if it upgrades then ok.  However, not sure how it will affect those packages.  Make sure all your data is **backed up**.

---

### Post by aktiwers on 2006-05-08
[quote=Sef]
Wine and theli are the problems.  If you have them on backports, you could unistall them and see if it upgrades then ok.  However, not sure how it will affect those packages.  Make sure all your data is **backed up**.[/quote]

So I should remove them from my sourcelist or apt-get remove them? 
Sorry, Im still a newbie..

Thanks

---

### Post by user1397 on 2006-05-08
[quote=aktiwers]So I should remove them from my sourcelist or apt-get remove them? 
Sorry, Im still a newbie..

Thanks[/quote]
Remove them from your sources.list, using:
```
sudo gedit /etc/apt/sources.list
```

---

### Post by aktiwers on 2006-05-08
[quote=erik1397]Remove them from your sources.list, using:
```
sudo gedit /etc/apt/sources.list
```[/quote]

Thanks a lot!

Upgrading now! :KS

---

### Post by xXx 0wn3d xXx on 2006-05-08
[QUOTE=aktiwers]Hi !

Im using Ubuntu Breezy 5.10 and are really thinking of upgrading to Dapper.

I have a few concerns though. 

1) Is it possible to apt-get from Breezy to Dapper? If yes, will I loose my current settings (home folder, installed aps ect..)?

Yes, but you will have a much slower system or your system may not even boot. Back up your /home folder and do a clean install of Dapper.

2) Will it be possible to apt-get remove back to breezy? Again without loosing current settings?

No, you will have to do a clean install of breezy.

3) Is it limited which programs I can use and install on Dapper, or is it the same as on Breezy? 

It is almost the same as breezy.

Thats my 3 primary concerns/questions about upgrading. I really want to try Dapper (with Xgl :P ) and other stuff, but are not sure if this is possible without  a reinstall.

Thanks a lot for reading.[/QUOTE]
Hope that helps.
Edit: Nevermind.

---

### Post by aktiwers on 2006-05-08
[quote=MasterChief1234]Hope that helps.
Edit: Nevermind.[/quote]

Thanks MasterChief! 

What do you mean with slower?

---

### Post by xXx 0wn3d xXx on 2006-05-08
[QUOTE=aktiwers]Thanks MasterChief! 

What do you mean with slower?[/QUOTE]
If you dist-upgrade there will be alot of clutter and junk left over so you will get decreased performance. I origionally did a dist-upgrade and then I did a clean install but the dist-upgrade was slow. Plus, by doing a clean install I didn't have to deal with the broken packages and all that stuff.

If you choose to dist-upgrade-install the ubuntu-desktop meta package (it will save you some headaches)

> sudo apt-get install ubuntu-desktop

---

### Post by browndog on 2006-05-08
[QUOTE=aktiwers]Hi !

Im using Ubuntu Breezy 5.10 and are really thinking of upgrading to Dapper.

I have a few concerns though. 

1) Is it possible to apt-get from Breezy to Dapper? If yes, will I loose my current settings (home folder, installed aps ect..)?

2) Will it be possible to apt-get remove back to breezy? Again without loosing current settings?

3) Is it limited which programs I can use and install on Dapper, or is it the same as on Breezy? 

Thats my 3 primary concerns/questions about upgrading. I really want to try Dapper (with Xgl :P ) and other stuff, but are not sure if this is possible without  a reinstall.

Thanks a lot for reading.[/QUOTE]
Honestly, the difference in comfort between Breezy and Dapper is huge!  I loved Breezy and didn't think Dapper would be that much of a difference, but it is!  Wait a couple of weeks, install the stable release and you'll be much happier.

---

### Post by aktiwers on 2006-05-08
Hmm thanks. 

But I believe its too late now ](*,) ?

I have some fast internet, and the installation is almost complete now.
I keep getting that wierd error messege though?

---

