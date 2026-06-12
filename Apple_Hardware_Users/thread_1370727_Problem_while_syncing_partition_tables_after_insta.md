---
title: "Problem while syncing partition tables after installing Ubuntu"
date: 2010-01-02
forum: Apple Hardware Users
---

### Post by Grayer on 2010-01-02
Hi,
Let me start off by giving an overview of my situation:
I have a macbook pro 13" from mid 2009 and I've been wanting to install Ubuntu for a while and I've been looking at many guides, one of them from this forum.  Maybe the way I installed Ubuntu is simply wrong so I'm going to list what I did.
1. Created a partition with bootcamp and installed rEFIT.
2. Used the try Ubuntu function and used the gparted tool in Ubuntu to erase the partition I created, hence leaving free space.
3. Installed Ubuntu selecting the option of use largest free space.  
4. I selected to install the grub to dev3/sda3.

After the installation is when the problem came... I restarted the computer and in rEFIT I cannot boot linux because it's not even there.  So I saw on a wepbage that there is a bug with Ubuntu and that I have to sync the partition tables.  However, when entering the partition tool in refit it gives me an error saying: 
"Status: GPT partition of type 'Uknown' found, will not touch this disk.
[COLOR=Red]Error: Not Found returned from gptsync.efi[/COLOR]
I have NO CLUE what this means and I've been searching the internet for hours but can't find the solution I'm getting so frustrated!!! Please can someone help?
Thanks and sorry for the long post...
EDIT: nevermind I solved the problem...

---

### Post by linuxopjemac on 2010-01-04
could you amend your post as being [SOLVED] ? Saves people reading things which are solved.

---

