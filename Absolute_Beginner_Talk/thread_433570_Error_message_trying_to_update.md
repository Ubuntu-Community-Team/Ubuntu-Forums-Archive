---
title: "Error message trying to update"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Done_Fishin on 2007-05-05
A pal who has a Ubuntu 7.04 install up & running gave me some advice saying I should install Automatix to get some really necessary updates etc.
I did this quite happily then used it to select several programs that I wanted to check out. One of these was Skype. When it came to the user agreement though I decided that i didn't really want to install it yet so I rejected the agreement, at which point things didn't go so well. It seemed that although I wanted to abort it insisted on continuing but left me hanging on some user page with <ok> at the bottom. No matter how many times I hit the <ok> it refused to go on and the whole system just hung in there refusing to continue with the other downloads I had asked for. Eventually, after waiting about an hour (I was working with my other PC) I hit the master reset button - Powered Off!
I am now in the position that when in either package manager or automatix I get an error when trying to do any updates.
an error occurred window pops up with

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

I have opened a terminal and tried to do this but with no success.
I get this response

> user@user-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
user@user-desktop:~$

So now I am wondering is this because of the aborted download, because of the hard power off, because I have 2 update managers ??
I looked for a way to uninstall Automatix but so far have found none.
I have looked for a tool to check the hard disk like one would in Windows that would allow me to check the file system & possible lost clusters but found none.
I created a UBCD 4.03 Live CD & used it to do some basic drive tests. I don't know enough Commands from Linux based systems to know what programs to call up or how to use them.

I have since tried to get into Synaptec Package manager to uninstall  but I get the same error.

I have found out that I needed to write sudo in front of the info I was told to write above to give me admin privileges. This brings me back up to the package configuration window of Skype where everything seemed to crash yesterday. THE <ok> at the bottom odf the page doesn't do anything and all I can do is close the window. Skype has been installed and I get to open the window to create an account. I can see no way of Un-installing in spite of checking out and doing what has been suggested in the skype help faq. I find no references to the un-install methods on my PC. Perhaps it is only partly installed.

---

### Post by STREETURCHINE on 2007-05-05
so what you do is run 

      ```
sudo dpkg --configure -a
```

in terminal,then

   ```
sudo aptitude update
```

and that should solve your problem

---

### Post by igknighted on 2007-05-05
just run the dpkg --configure -a command as root (w/ sudo), accept the license for now, then delete it later if you really want to.

---

### Post by L Campbell on 2007-05-05
> **Done_Fishin said:**
> A pal who has a Ubuntu 7.04 install up & running gave me some advice saying I should install Automatix to get some really necessary updates etc.
I did this quite happily then used it to select several programs that I wanted to check out. One of these was Skype. When it came to the user agreement though I decided that i didn't really want to install it yet so I rejected the agreement, at which point things didn't go so well. It seemed that although I wanted to abort it insisted on continuing but left me hanging on some user page with <ok> at the bottom. No matter how many times I hit the <ok> it refused to go on and the whole system just hung in there refusing to continue with the other downloads I had asked for. Eventually, after waiting about an hour (I was working with my other PC) I hit the master reset button - Powered Off!
I am now in the position that when in either package manager or automatix I get an error when trying to do any updates.
an error occurred window pops up with



I have opened a terminal and tried to do this but with no success.
I get this response



So now I am wondering is this because of the aborted download, because of the hard power off, because I have 2 update managers ??
I looked for a way to uninstall Automatix but so far have found none.
I have looked for a tool to check the hard disk like one would in Windows that would allow me to check the file system & possible lost clusters but found none.
I created a UBCD 4.03 Live CD & used it to do some basic drive tests. I don't know enough Commands from Linux based systems to know what programs to call up or how to use them.

I have since tried to get into Synaptec Package manager to uninstall  but I get the same error.

I have found out that I needed to write sudo in front of the info I was told to write above to give me admin privileges. This brings me back up to the package configuration window of Skype where everything seemed to crash yesterday. THE <ok> at the bottom odf the page doesn't do anything and all I can do is close the window. Skype has been installed and I get to open the window to create an account. I can see no way of Un-installing in spite of checking out and doing what has been suggested in the skype help faq. I find no references to the un-install methods on my PC. Perhaps it is only partly installed.

This is slightly off your topic here but, if you want Skype (or Gizmo), you don't need Automatix to install it, in my experience.

Just go to their website and you can download their program.  It is straightforward to install.

---

### Post by Done_Fishin on 2007-05-05
> **STREETURCHINE said:**
> so what you do is run 

      ```
sudo dpkg --configure -a
```

in terminal,then

   ```
sudo aptitude update
```

and that should solve your problem

Unfortunately it didn't.
The Skype Package config dialogue opened again.
I cleared it and added the 2nd line you gave me and the rsult was to return me to the original statement inside the terminal window - unable to update cache.

---

### Post by Done_Fishin on 2007-05-05
> **igknighted said:**
> just run the dpkg --configure -a command as root (w/ sudo), accept the license for now, then delete it later if you really want to.
I can't find away to go either forwards or back on this and any attempt to install or re-install aborts for the same error as listed at the start.

---

### Post by STREETURCHINE on 2007-05-05
go to the automatix web forum there is a link in my signature and arnie boy will sort it for you:)

---

### Post by Done_Fishin on 2007-05-05
> **L Campbell said:**
> This is slightly off your topic here but, if you want Skype (or Gizmo), you don't need Automatix to install it, in my experience.

Just go to their website and you can download their program.  It is straightforward to install.

That is besides the point. How one makes the upgrade or install is irrelevant when you have done it and it messes everything up .. 
Whether  you buy your sweets or candies at Supermarket or Corner shop  doesn't make any difference when you have the bag in your hand but something is stopping you from opening it!
I want to clear up the mess I have made then I can start over.

---

### Post by Done_Fishin on 2007-05-05
> **STREETURCHINE said:**
> go to the automatix web forum there is a link in my signature and arnie boy will sort it for you:)

I am using Ubuntu 7.04 where should I post this question plus this response happens when trying to upgrade from the add/remove in Applications, Automatix AND Synaptic Package Manager ( System)

Ignore that above ... just found the forum (hopefully)

---

### Post by STREETURCHINE on 2007-05-05
the automatix team are very helpfull with any problem not just one to do with automatix,

---

### Post by Done_Fishin on 2007-05-05
> **STREETURCHINE said:**
> the automatix team are very helpful with any problem not just one to do with automatix,

Thanks
I have put my "tale of woe" on the feisty support and I will post back here with any progress I make. it's not a total disaster for me because i am working off of a couple of Hard disks with a clone of a  working environment kept safely on a second disk. Going back is as easy as copying the working partition to the "work horse" but that's the easy way and you don't learn anything by doing it!:) 
Thanks to all for any help and also please if anyone has a idea about this that hasn't been said, and you feel like helping .. spit it out!
Tx

---

### Post by Done_Fishin on 2007-05-05
It seems that there are some things that we have to learn the hard way. 
I had been trying to click on the <ok> but it did nothing.
During the time I had tried to sort out this problem I had been cruising around reading bits & pieces (including the helpfiles) and I had read that you can "TAB" between open terminals. I had opened a separate terminal to run the

> sudo aptitude update

because I couldn't find a way to get away from the package configuration & EULA without either doing a reset or closing the window.
Thsi time around though when I went to get the quote from the error box I hit the tab thinking it might take me back to the command line of terminal. However what it did instead was to highlight the <ok> so that I could refuse and therefore bypass that part of the setup. There were NO instructions on the page to say what to do!!!
So I have now managed to proceed to the point where I can get back into the update process.
New one that for me !!

The Problem's over .. I put it down to poor learning or poor instruction!
Thanks for all your help.

---

### Post by L Campbell on 2007-05-05
> **Done_Fishin said:**
> That is besides the point. How one makes the upgrade or install is irrelevant when you have done it and it messes everything up .. 
Whether  you buy your sweets or candies at Supermarket or Corner shop  doesn't make any difference when you have the bag in your hand but something is stopping you from opening it!
I want to clear up the mess I have made then I can start over.

As I said, my reply was slightly off topic but I thought it might be of interest to you.

Sorry I ruined your day.

---

### Post by Done_Fishin on 2007-05-06
> **L Campbell said:**
> As I said, my reply was slightly off topic but I thought it might be of interest to you.

Sorry I ruined your day.

My apologies **_to you_** Lewis, You didn't ruin my day, I was and always will be, appreciative of any support I get about stuff I don't know. "Out of context" the bit you quoted of my reply sounds really gruff and it wasn't meant to be.  That's the worst with the written word, you can't flavour it with accents. Every time I try to chat I find myself battling with ways to use emoticons but since some sites have a click and add, some have a drag & drop, others have a click, read the code / remember it then write it in the box method, I regret I don't use them 
Please accept my sincerest apologies for offending you and don't hold a grudge against me for my stupid mistake.:) :)

---

### Post by L Campbell on 2007-05-08
> **Done_Fishin said:**
> My apologies **_to you_** Lewis, You didn't ruin my day, I was and always will be, appreciative of any support I get about stuff I don't know. "Out of context" the bit you quoted of my reply sounds really gruff and it wasn't meant to be.  That's the worst with the written word, you can't flavour it with accents. Every time I try to chat I find myself battling with ways to use emoticons but since some sites have a click and add, some have a drag & drop, others have a click, read the code / remember it then write it in the box method, I regret I don't use them 
Please accept my sincerest apologies for offending you and don't hold a grudge against me for my stupid mistake.:) :)

OK, no problem.

Sorry it took me so long to see your message here.

Kind regards.

---

