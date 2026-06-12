---
title: "Internet Slowness with Dapper Drake"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by Jameson_Styles on 2007-03-15
I installed Ubuntu 6.06, and was pleased to find that it works... for the most part. The firefox internet browsing is INCREDIBLY slow, and I have no idea why. I know I have connectivity because it found Newegg.com (showed me "once you know, you newegg" something it could only know if it was able to connect) but after 5 minutes of loading the progress bar had barely crawled half way across. 

I have full DSL broadband, and I have never had any connectivity issues with the computer before.

I was thinking it was the lack of motherboard drivers, but to install them I need ubuntu to read .dll and .exe, which it doesn't. 

Any tips?

---

### Post by DaveyG on 2007-03-15
Umm.. i dont know why that is but try this..

type: about:config in the browser,

right click, then new, then Integer,
Name the integer: nglayout.initialpaint.delay
Set the integers value to: 0
See if that makes a differance

Davey

---

### Post by Jameson_Styles on 2007-03-15
Nope, didn't help

It looks like it's going to make it to newegg.com... it really does. It's trying, I swear it is, but it just never quite does it...

I'm baffled. Do you think there's anything to my motherboard drivers theory?

---

### Post by DaveyG on 2007-03-15
newegg.com loads pretty fast for me..
what sort of internet connection do you have? have you downloaded the latest drives for your internet card? are you using wireless or ethernet?

Edit: Sorry didnt read the first post properly

Are you using your modem via the phone line?

Davey

---

### Post by Jameson_Styles on 2007-03-15
Oh, it isn't just newegg, it's every website, even ubuntu.com.

I run ethernet into my onboard ports

Unless ubuntu has ethernet drivers included with it, I have no drivers whatsoever, which is probably my problem. Trouble is, I have no way of installing drivers for my motherboard because they have .exe's and .dll's

Not sure how to get Wine to that computer as I am completely out of cd-r's...

Flash Drive! I'll install Wine on the other computer and let you know if installing drivers fixes my problem.

---

### Post by Jameson_Styles on 2007-03-15
Okay, I saved Wine onto my flash drive and installed it on the other computer... now how do I make it work? 
I still can't run exe's which makes me think that I have to do something to turn on Wine. Trouble is, I can't even find the program after I've installed it! What folder does Wine typically install to?

---

### Post by r4ik on 2007-03-15
> **Jameson_Styles said:**
> I installed Ubuntu 6.06, and was pleased to find that it works... for the most part. The firefox internet browsing is INCREDIBLY slow, and I have no idea why. I know I have connectivity because it found Newegg.com (showed me "once you know, you newegg" something it could only know if it was able to connect) but after 5 minutes of loading the progress bar had barely crawled half way across. 

I have full DSL broadband, and I have never had any connectivity issues with the computer before.

I was thinking it was the lack of motherboard drivers, but to install them I need ubuntu to read .dll and .exe, which it doesn't. 

Any tips?


Try,

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29)

good luck !

---

### Post by Jameson_Styles on 2007-03-15
Thank you for your help, but I'm not entirely sure what to do with the information there.

"for ubuntu 

1. gksudo gedit /etc/modprobe.d/bad_list  

2. Add this line:  alias net-pf-10 off  

3. Save the file and restart your computer" 

I'm sure that for someone with experience that this would be a very simple task, but I haven't the slightest idea what to do, or even where to begin. If someone could maybe type out some instructions for how to proceed, I would really, REALLY appreciate it.

Thank you for putting up with my lack of knowlege.

---

### Post by Jameson_Styles on 2007-03-15
Wait, I'm using Dapper... these are the instructions it gave for it.

"for ubuntu 

1. gksudo gedit /etc/modprobe.d/aliases 

2. Comment out this line:  alias net-pf-10 ipv6  

3. Save the file 

4. gksudo gedit /etc/modprobe.d/blacklist 

5. Add this line:  blacklist ipv6  

6. Save the file and restart your computer" 

Yeah... I'm lost. Again, if someone could type out instructions for how I should proceed I would really, truly appreciate it from the deepest depths of my heart.

---

### Post by r4ik on 2007-03-15
Use the Terminal to put in the commands,

 gksudo gedit /etc/modprobe.d/aliases 


Comment out by putting # in front of a line.

gksudo gedit /etc/modprobe.d/blacklist 


add blacklist ipv6 at the bottem of the file.

---

### Post by freebird54 on 2007-03-15
Didn't know that Dapper had this problem - but it is worth a try.  First open up a terminal.  It is found in Applications->Accessories->Terminal.

Then enter this code at the prompt (you could paste it, or re-type it - your choice. (Keyboard paste is <ctrl><shift>v  or use menu)

```

gksudo gedit /etc/modprobe.d/aliases
```

and hit <enter>.  An editor (notepad-like) will open with the aliases file in it.  You need to comment out the entry as shown (# is the comment marker)

```
alias net-pf-10 ipv6
```

making it:

```
#alias net-pf-10 ipv6
```

and then add these lines (without extra spaces or changes)

```
alias net-pf-10 ipv6 off 
alias net-pf-10 off 
alias ipv6 off
```

Save and exit the editor.  Then try editing this file:

```
gksudo gedit /etc/modprobe.d/blacklist
```

and add

```
blacklist ipv6
```

It may be the first entry - but that's fine.

Save the file, exit,  ( and typeing exit closes the terminal too) then reboot your computer. Is the net any quicker?

Between those 2 you should be back at full speed. Actually - the first one should work by itself.  Good luck from a fellow newbie!

---

### Post by Jameson_Styles on 2007-03-15
That did it! Thank you sooo much!

It works just fine now, the net loads pages just as quick as I would expect it to.

So there's my first real experience with terminal... that was fun.

---

### Post by r4ik on 2007-03-15
> **freebird54 said:**
> Didn't know that Dapper had this problem - but it is worth a try.  First open up a terminal.  It is found in Applications->Accessories->Terminal.

Then enter this code at the prompt (you could paste it, or re-type it - your choice. (Keyboard paste is <ctrl><shift>v  or use menu)

```

gksudo gedit /etc/modprobe.d/aliases
```

and hit <enter>.  An editor (notepad-like) will open with the aliases file in it.  You need to comment out the entry as shown (# is the comment marker)

```
alias net-pf-10 ipv6
```

making it:

```
#alias net-pf-10 ipv6
```


and then add these lines (without extra spaces or changes)

```
alias net-pf-10 ipv6 off 
alias net-pf-10 off 
alias ipv6 off
```

Save and exit the editor.  Then try editing this file:

```
gksudo gedit /etc/modprobe.d/blacklist
```

and add

```
blacklist ipv6
```

It may be the first entry - but that's fine.

Save the file, exit,  ( and typeing exit closes the terminal too) then reboot your computer. Is the net any quicker?

Between those 2 you should be back at full speed. Actually - the first one should work by itself.  Good luck from a fellow newbie!

Cristal clear,

Thanks !

---

### Post by freebird54 on 2007-03-15
You're very welcome.  I just tried to remember what my first few hours on this system were like :D

---

### Post by 146lily on 2007-03-16
This is an old problem with suse, a quick fix in firefox is to enter **about:config**  in the browser and change the setting in the long list for **network.dns.disableIPv6** to **true**.You will now be able to browse better for globally disabling ipv6.
So some one comes up with ipv6 and them claims all are linux applications are broken because they dont work with this piece of rubbish software. What amazes me is that this does not happen to microsoft and is well know in linux, maybe some people want to  f--k linux.

---

