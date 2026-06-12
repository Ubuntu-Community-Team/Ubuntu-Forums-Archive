---
title: "questions about beryl"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by dragnazz5.0 on 2007-01-23
well ive looked through the installation guides and just about everything i can understand about beryl.  my question is, do i need a good graphics card to run beryl?  or can i just run it on my computer without any problems.  im always looking for something cool to do with my computer and i think this is something i want to do but im kind of unsure how to go about diong it....if i can at all.  ive got a toshiba laptop that is about 4 years old so its not the newest of the new and definetly a little outdated but it runs great and never has any overloading or overheating issues.  how do i go about installing beryl? or is there something similar that i can use?  sorry for the stupid newbie post but there are just a lot of things that i dont understand in the other posts so any laymans terms you can use will really help me.  thanks again guys.

---

### Post by 23meg on 2007-01-23
What video chip do you have in your laptop?

---

### Post by sardion on 2007-01-23
I use Beryl with a slow computer.  600MHz processor.  Intel graphics chip 64MB RAM.  It's a little slow, but it works fine.

To get beryl going, visit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) and follow the instructions there to add their repos to your list.

After that, just run "beryl-manager" from a terminal and see how you like it.

---

### Post by dragnazz5.0 on 2007-01-23
> **23meg said:**
> What video chip do you have in your laptop?

i have no idea...i know im retarded

---

### Post by dragnazz5.0 on 2007-01-23
> **sardion said:**
> I use Beryl with a slow computer.  600MHz processor.  Intel graphics chip 64MB RAM.  It's a little slow, but it works fine.

To get beryl going, visit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) and follow the instructions there to add their repos to your list.

After that, just run "beryl-manager" from a terminal and see how you like it.

well it wont let me change the /etc/apt/sources.list for some reason.  i just added wine to it the other day and now it wont let me change it.

---

### Post by 23meg on 2007-01-23
> **dragnazz5.0 said:**
> i have no idea...i know im retarded
Go to System / Administration / Device Manager and see what it is.

---

### Post by 23meg on 2007-01-23
> **dragnazz5.0 said:**
> well it wont let me change the /etc/apt/sources.list for some reason.  i just added wine to it the other day and now it wont let me change it.What error are you getting when trying to change it? Are you using sudo/gksudo?```
gksudo gedit /etc/apt/sources.list 
```

---

### Post by dragnazz5.0 on 2007-01-23
radeon mobility m6 LY?  i think thats it.

---

### Post by dragnazz5.0 on 2007-01-23
> **23meg said:**
> What error are you getting when trying to change it? Are you using sudo/gksudo?```
gksudo gedit /etc/apt/sources.list 
```

alright, im really retarded. i dont know why i forgot the sudo gedit

alright...now which link do i click on in the repository page you sent me?

when i run sudo apt-get update i get this error at the bottom

W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: You may want to run apt-get update to correct these problems

---

### Post by NewOldTimer on 2007-01-23
Hey fellow n00b, just finished installing beryl, quite happy with the results{thank-you Forum}. I used this page to help me walk thru the steps on me "Edgy" set-up. Hope this will help...
[http://doc.org/index.php/berylonedgy](http://doc.org/index.php/berylonedgy) ,  Sorry for the sad attempt at a link I'm so new I still have the plastic around my head.

---

### Post by dragnazz5.0 on 2007-01-23
> **NewOldTimer said:**
> Hey fellow n00b, just finished installing beryl, quite happy with the results{thank-you Forum}. I used this page to help me walk thru the steps on me "Edgy" set-up. Hope this will help...
[http://doc.org/index.php/berylonedgy](http://doc.org/index.php/berylonedgy) ,  Sorry for the sad attempt at a link I'm so new I still have the plastic around my head.

thanks for the link but im running dapper

---

### Post by dragnazz5.0 on 2007-01-23
nevermind...i finally figured out that synaptic had the packages.  now i just have to figure out how to get it working

---

### Post by dragnazz5.0 on 2007-01-23
well i got the manager working but when i try to select the beryl window manager all the windows just flash and it doesnt do anything

if i type sudo beryl in terminal i get this

XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension

---

### Post by NewOldTimer on 2007-01-23
Hey Again dragnazz5.0, 
hope I'm not adding to the problems but this post from Pricechild has some very interesting reads, you might want to give it the ol once over...[http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

Just throwing my 2 cents in

---

### Post by dragnazz5.0 on 2007-01-24
i just upgraded to edgy eft so hopefully i can follow the instructions you gave before to get it working.  thanks for the other link also

---

