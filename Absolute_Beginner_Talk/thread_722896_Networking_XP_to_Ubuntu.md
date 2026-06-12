---
title: "Networking XP to Ubuntu"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Literati on 2008-03-12
Believe it or not. I DID search.

What I'm looking to accomplish is this.

I have a Linksys WRT300N Wireless Router.
I have 3 computers in the house:

- 1 Desktop (Wireless Connection) (Windows XP)
- 1 Desktop (Wired Connection) (Ubuntu)
- 1 Laptop (Wireless Connection) (Windows XP)

I would like EVERY computer on the network to be able to see, copy, and move files on every other computer on the network if they should so need to do so.

Now, how exactly would I go about that?

---

### Post by thisiam on 2008-03-12
search for SAMBA.

---

### Post by joshrobinson on 2008-03-12
click system, administration, shared folders
it will come up saying it wants to install samba, install the packages
click the general properties tab, and make sure your on the same workgroup as the other computers
on the shared folders tabs, add the folders you want to share

this should let you see your other computers now, but you may have to add a user account so the other computers can see your ubuntu install

let me know how far you get, and whats going on.. ill try to help from there

---

### Post by Literati on 2008-03-13
> **joshrobinson said:**
> click system, administration, shared folders
it will come up saying it wants to install samba, install the packages
click the general properties tab, and make sure your on the same workgroup as the other computers
on the shared folders tabs, add the folders you want to share

this should let you see your other computers now, but you may have to add a user account so the other computers can see your ubuntu install

let me know how far you get, and whats going on.. ill try to help from there

Alright, this worked fine, I'm even playing music that stored on my Ubuntu computer off of my Windows Laptop. :) 

I'm trying to view my other Desktop computer from my Ubuntu setup through NETWORK. 
I can access the laptop just fine (No passwords on users on Windows) 
But I get a password popup for the other computer. It DOES have passwords on that windows setup, but I tried my own password (on Ubuntu) and the password I use on that machine, and NEITHER of them let me sign in. Any ideas?

Thanks!

EDIT: I've fixed it, and everything is networked now. That was relatively painless (Easier than linking the three XP systems we had before! :D)
Thank you very much :)

---

### Post by kulotzy on 2008-03-20
> **Literati said:**
> Alright, this worked fine, I'm even playing music that stored on my Ubuntu computer off of my Windows Laptop. :) 

I'm trying to view my other Desktop computer from my Ubuntu setup through NETWORK. 
I can access the laptop just fine (No passwords on users on Windows) 
But I get a password popup for the other computer. It DOES have passwords on that windows setup, but I tried my own password (on Ubuntu) and the password I use on that machine, and NEITHER of them let me sign in. Any ideas?

Thanks!

EDIT: I've fixed it, and everything is networked now. That was relatively painless (Easier than linking the three XP systems we had before! :D)
Thank you very much :)

Im interested in how you fixed it... i cant seem to log in to my Ubuntu PC from my Vista. Im trying to log in using my Ubuntu username and password. What am i doing wrong?

---

### Post by bigken on 2008-03-20
in a terminal type 

sudo smbpasswd -e (your name)

sudo smbpasswd -a (your name)

---

### Post by Nermi on 2008-03-22
> **joshrobinson said:**
> click system, administration, shared folders
it will come up saying it wants to install samba, install the packages
click the general properties tab, and make sure your on the same workgroup as the other computers
on the shared folders tabs, add the folders you want to share


I was hoping that this would solve my problem too. However, when I did what you suggested -click system ->admin ->shared folders, I get a prompt "Shared services not installed", "You need to install either Samba or NFS"... and then both SMB and NFS are checked and when I click to install... I get the same prompt over and over again. It didn't change anything if I unchecked any of the boxes. 

What am I doing wrong?

Thank you, 

Nermi

---

### Post by bigken on 2008-03-22
> **Nermi said:**
> I was hoping that this would solve my problem too. However, when I did what you suggested -click system ->admin ->shared folders, I get a prompt "Shared services not installed", "You need to install either Samba or NFS"... and then both SMB and NFS are checked and when I click to install... I get the same prompt over and over again. It didn't change anything if I unchecked any of the boxes. 

What am I doing wrong?

Thank you, 

Nermi


you could try this open a terminal and type 

sudo apt-get install samba

---

### Post by chlorinekid on 2008-03-22
chck this video out. it worked wonders for me pal

[http://youtube.com/watch?v=Ad17kma8rNM](http://youtube.com/watch?v=Ad17kma8rNM)

---

### Post by Nermi on 2008-03-22
> **bigken said:**
> you could try this open a terminal and type 

sudo apt-get install samba
This is what happens:
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  smbclient samba-common
E: Package samba has no installation candidate

Then I try:
sudo apt-get install smbclient samba-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
smbclient is already the newest version.
samba-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

???, Thanks

Nermi

---

### Post by Nermi on 2008-03-22
> **chlorinekid said:**
> chck this video out. it worked wonders for me pal

[http://youtube.com/watch?v=Ad17kma8rNM](http://youtube.com/watch?v=Ad17kma8rNM)

It's all great but when I come to the part when I enter System -> Administration ->Shared Folders... it asks me to install NFS or SMB and when I click "Install Services" it keeps looping back to the same prompt... 


Nermi

---

### Post by chlorinekid on 2008-03-22
do you need to select something before you click "install services"?

you could try installing samba beforehand as outlined in some previous posts.

---

### Post by Nermi on 2008-03-22
> **chlorinekid said:**
> do you need to select something before you click "install services"?

you could try installing samba beforehand as outlined in some previous posts.

Yes, when I am promted to 'install services',  it asks me to install NFS or SMB or both? And both is already checked for me. And it doesn't make a difference if I uncheck any of them... I get back to the same prompt. 

And I did try to install Samba first and this is what I get:

Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
smbclient samba-common
E: Package samba has no installation candidate

Then I try:
sudo apt-get install smbclient samba-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
smbclient is already the newest version.
samba-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


And, thank you very much for your help. 


Nermi

---

### Post by bigken on 2008-03-23
have you tried sudo apt-get install samba ?

also have you checked your repoistories list

---

### Post by swotie on 2008-03-23
I have followed this instructions video [url="http://youtube.com/watch?v=Ad17kma8rNM"]http://youtube.com/watch?v=Ad17kma8rNM[/URL

I find all my computers (1 unbuntu (desktop) 1 win xp home (desktop) 1 win xp home (laptop) in my SMB network at my ubuntu machine .. The Network group name is "Mshome" ....

But then I go to the 2 windows machine and will access the workgroup Mshome .... I receive a answer ..

"Mshome isn't avaible ... perhaps You don't have permission to use this network resource ... contact your admin ... ect.

The account has no authority to log on from this computer"

What do I wrong
__________________

---

### Post by bigken on 2008-03-23
> **swotie said:**
> I have followed this instructions video [url="http://youtube.com/watch?v=Ad17kma8rNM"]http://youtube.com/watch?v=Ad17kma8rNM[/URL

I find all my computers (1 unbuntu (desktop) 1 win xp home (desktop) 1 win xp home (laptop) in my SMB network at my ubuntu machine .. The Network group name is "Mshome" ....

But then I go to the 2 windows machine and will access the workgroup Mshome .... I receive a answer ..

"Mshome isn't avaible ... perhaps You don't have permission to use this network resource ... contact your admin ... ect.

The account has no authority to log on from this computer"

What do I wrong
__________________


try running the network wizard in my network places

---

### Post by swotie on 2008-03-23
don't work ...

---

### Post by bigken on 2008-03-23
have you rebooted the pc ?

---

### Post by swotie on 2008-03-23
yes .. I have rebooted 

if I from win xp laptop search for win xp desktop computer, I find it and can access it.

If I from win xp laptop search for ubuntu computer, I find it but can't access it

If I from win xp desktop search for win xp laptop,I find it and can access it.

If I from win xp desktop search for ubuntu computer, I find it but can't access it

From ubuntu computer I find all 3 computers in Mshome network , and can access both windows computers

---

### Post by tad1073 on 2008-03-23
If you are behind a firewall you need to configure it or turn it off for testing purposes.

---

### Post by swotie on 2008-03-23
I have no firewall

---

### Post by bigken on 2008-03-23
> **bigken said:**
> in a terminal type 

sudo smbpasswd -e (your name)

sudo smbpasswd -a (your name)


you need to run these commands in a terminal

---

### Post by tad1073 on 2008-03-23
Have you set-up a user for samba?

> **bigken said:**
> in a terminal type 

sudo smbpasswd -e (your name)

sudo smbpasswd -a (your name)

---

### Post by pbpersson on 2008-03-23
Speaking of firewalls, when I attempt this sort of stuff I turn off the firewalls on all the machines.

I make sure my wireless network is secure so no one can break in

I make sure I am buffered from the Internet by a gateway so no one can get to my internal network

Otherwise.....if you have the firewalls enabled on each machine you would need  to open the file sharing IP ports on each one and this is something I have never done.

My view is that either you can be completely secure or you can be productive - the two are mutually exclusive so I usually run with as little security as possible so I can get my work done.  

I was going to add an emoticon but I didn't know what to add - this seems sad and glad at the same time.  :confused:

---

### Post by tad1073 on 2008-03-23
I use firestarter on ubuntu and norton on windows. I had the same problems descibed in this about mshone not accessable but once I configured norton it worked. Another problem I had was when I was following the wiki about iptables and didn't flush the rules I put in before I configured firestarter.

---

### Post by pbpersson on 2008-03-23
> **tad1073 said:**
> Have you set-up a user for samba?

Yeah - editorial comment - that is dumb

I know I am probably preaching to the choir

However, I setup SAMBA and it said everything was good to go and I was golden

**NOWHERE** did it say "oh, by the way, if you don't add a default SAMBA user this will never work"

Someone needs to fix this

I only discovered it by checking this forum and when I saw it I remembered setting up SAMBA years ago and I was like, "Oh yeah.....the default SAMBA client account it passes to Windows....I remember now"

I view this as another hole we need to plug that users are falling into :(

---

### Post by swotie on 2008-03-23
I have tried to set up samba with these commands again ... it don't help

---

