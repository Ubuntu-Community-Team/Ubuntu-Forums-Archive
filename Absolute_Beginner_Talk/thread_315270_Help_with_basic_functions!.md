---
title: "Help with basic functions!"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by say592 on 2006-12-08
I have been a windows user for as long as I have used a computer, my windows system caught a virus, and completely corrupted the log-in files.

All of that aside, I made the switch from a recommendation from a user on my psp forums, he suggested I use the live version, try to find the virus in windows, then deleate it, and go back to XP. I fell in love with the interface and am planning on restoring XP but using this for all functions other than those that require xp. 

1. I have ubuntu on my "e" disk in windows (secondary hdd) I want to use the other hdd and install a third, how? I need a walkthrough step by step because this is not like I am used to.
2. I want to run/install some of my windows apps, I am sure there is a way to do this, but what is required?
3. I havent installed Firefox extensions in about one year, so I dont remember whether they all work on all versions or whether I need a linux version. I went to the site and clicked install on two of the ones I used before, and they downloaded and worked after I started FF like normal, so can I use all of the same?
4. I heard about easyubuntu. It isnt so easy if you have no clue about linux! Could I have some help with this? 

I was windows literate, so I am not an idiot around a processor....

I would appreciate help in all forms! I love to use AIM or another service when getting help, so if you can help me that way let me know! Thanks!

PS. Has anyone ever gotton an error when booting up the computer that there was a fan error? I had this pre-linux but alot of you have custom PCs so I thought you might know......

---

### Post by say592 on 2006-12-08
Correction, one of the extensions I installed was add-block, it crashes FF whenever I go to a page that has an add! Another thing I need help with lol

---

### Post by mongooseman1128 on 2006-12-08
okay, for general knowledge, I have some greats links
> [http://www.linuxnewbieguide.org/](http://www.linuxnewbieguide.org/)
> [http://www.unix-tutorials.com/tutorials.php?os=Ubuntu](http://www.unix-tutorials.com/tutorials.php?os=Ubuntu)
> [http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)
> [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
Those tutorials are pretty awesome for new users.
as far as your point number one could you tell me exactly what it is you're trying to accomplish? And the logical and physical layout of your drives (just in case it's important)

---

### Post by MacD on 2006-12-08
Hi- welcome to the community.  :) 

It's probably best to post your questions as individual threads. You are biting off a pretty good sized bunch of stuff all at once. Change a lot of stuff at once and you will run into problems. I'm a Ex Windows power user now using ubuntu for a couple of months... and I'm still learning about basic stuff.

Wine will run some windows programs... many of your programs probably have linux equivalents that are just as good. look around in the synaptic package manager or in the forums if you have specialized needs.  You will have to be patient and realize that "different" is not "better/worse"...

I have come to really appreciate the huge variety of apps in synaptic, and the lack of commercial upgrade options on everything.

---

### Post by mongooseman1128 on 2006-12-08
yeah MacD was definitely right about that one. to add on, always make sure that your thread title is descriptive of your problem. This helps people to know what threads they can and cannot be helpful with.

---

### Post by MacD on 2006-12-08
RE: easyubuntu

automatix does a lot of the same stuff.

One thing about easyubuntu:
There is a point where it just hangs.  It wants you to enter your password but doesn't prompt you for it.  Watch the progress in the terminal.  If, early on in the process, it doesn't seem to be doing anything, try entering your password.

---

### Post by mongooseman1128 on 2006-12-08
As far as the extension that's freezing up FF, I'd suggest going to preferences and turning stuff off then manually block ads on pages Otherways, I would suggest just uninstalling it. to do this go to tool > Extensions then click the extension and then uninstall.

---

### Post by say592 on 2006-12-08
Got FF working, (uninstalled, remembered that before read post :)) and I want to know where to put the files for limewire (i havent used it before, i dont pirate things, my friend said once its installed he can help) I have the file unzipped and on the desktop, where to I move it?

---

### Post by say592 on 2006-12-08
What do you meant the layout of my drives? The linux one is slave, windows is master, i can look up the partitions if thats what you want...........

---

### Post by say592 on 2006-12-08
FF still crashes, no extensions, nothing, It just crashes :(

---

### Post by mongooseman1128 on 2006-12-10
If by crashing you mean you're not getting to any web pages at all, the common fix for this is to go to the URL bar and type "about:config" then as a filter type "ipv6" and double click the line that comes up so that it says true. However, if it's just not opening, I don't know how well this will work but try going to Synaptic packet manager (found in system > administration) and search for Firefox. when the search finishes mark the top package (description should be: "lightweight web browser based on Mozilla") for reinstallation (click the green box) and then hit apply.

---

### Post by mongooseman1128 on 2006-12-10
(this is in reply to your first point in the original post) for the layout of your drives, is there only one partition per drive? and the Ubuntu drive is slaved to the Windows one? What is the end result you're hoping for?

---

