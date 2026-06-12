---
title: "How do you Kill Ubuntu (x/K)"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by Breeegz on 2006-10-18
Ok, I'm a total linux newb, on my 4th self inflicted full install of Ubuntu.  As much as I'd like to I'd rather not kill ubuntu with the Trial and error method, I'd rather avoid stupid things that you can do to break Ubuntu bad enough that I cannot fix and need to reinstall.

I tried searching and concluded that a list like this doesn't exist, does anyone have a link?  If not then we should start one (NEWBS + NEWBS = newbs helping each other)

I will start

1. Do not reconfigure X Server unless you know what the settings do...  I couldn't log on after changing my login mode...

---

### Post by gustolove on 2006-10-18
Normally it is best to either ask if something will work on the forums before you try it if you are not sure.

Also Automatix makes life easier in some ways.

---

### Post by Breeegz on 2006-10-18
I'm sure asking helps, maybe I'll do that next time...   I just figured that I'd try a couple of seemingly insignificant things and Whamo, I'm completely over my head:-k  I det to the point that I don't even know what question to ask (after I break Ubuntu)

Don't get me wrong, I like Ubuntu, I just wished I could read a thread with a couple "What not to do" situations so I can watch out for them.  I'm sure there is too many to list, but I keep on finding them.

---

### Post by gustolove on 2006-10-18
since Ubuntu is completely customizable/changable it is relatively easy to edit something incorrectly and get results that were opposite of what you were hoping for. 

I remember when I was configuring my computers X server to get SLI working properly and it took me quite a while of searching on the forums.

---

### Post by x64Jimbo on 2006-10-18
Your best bet is to always back up your config files when you edit them. That way even if you completely hose your system, you can boot to the recovery console and copy them back to their original locations and everything will work again.

---

### Post by pay on 2006-10-18
You can easily change the system back to the way it was aslong as you have the terminal. Ie if i edited /etc/X11/xorg.conf and then I didn't have my display working I could then open that file using the terminal "sudo nano /etc/X11/etc/xorg.conf" and remove the changes that I made.

---

### Post by HermitDragon on 2006-10-18
The only reason that is easy for you is not because you have the terminal but because you know the command lines.

---

### Post by pay on 2006-10-18
Welcome to the forums HermitDragon.
You have a good point but that's why this forum is here so people can learn the command line. I would say it would be easier if you broke your system to post the problem here and ask for help then have someone show you how to fix it then you will learn abit more and have you system back instead of having to rebuild it everytime something goes wrong.

---

### Post by HermitDragon on 2006-10-18
True enough that coming here is a help and does get one familar with things. 

I would add to the list of things not to do: Don't add Nvidia drivers before updating the OS... and then make sure they work for the 64 bit system if thats what your using.

Doing that causes an inability for the system to locate any usable screens. I don't know if there is a way to remove them from what appears to be Ubuntu's version of safe mode.

---

### Post by x64Jimbo on 2006-10-18
> **pay said:**
> Welcome to the forums HermitDragon.
You have a good point but that's why this forum is here so people can learn the command line. I would say it would be easier if you broke your system to post the problem here and ask for help then have someone show you how to fix it then you will learn abit more and have you system back instead of having to rebuild it everytime something goes wrong.
Pay is right. Linux is a DIY operating system in many ways. Sure there are a lot of really cool automated scripts and things out there to get your system running the way you want it, but for the most part, the community remains the same - tinkerers. People who like to take it apart and put it back together. I believe you'll find the best results with Linux if you put your best efforts into learning what the commands are doing, rather than just copy-pasting them.

---

### Post by Coelocanth on 2006-10-18
> **Breeegz said:**
> 

1. Do not reconfigure X Server unless you know what the settings do...  I couldn't log on after changing my login mode...

I figure this is probably axiomatic. Why would one change settings *without* knowing what they do?

As a corollary to that:

1a. Ask before you change settings, if you're unsure what they do. This could potentially save you a lot of grief.

That being said, there's nothing like learning from mistakes. If you don't have any worries about data loss, breaking your installation can be an effective way to learn (just as long as you remember what you did to 'break' it, so you can research what went wrong).

---

### Post by Breeegz on 2006-10-19
^True, I know enough not to play aound in the regristry in windows, doing so is a sure fire way to hose you windows installation if you do not know what you are doing.

The setting I changed seemed self explanatory, on the login window GUI, from something (default) to chooser (I'm on my other computer --Windows-- so I cannot quickly check the setting, but that's neither here nor there) 

Well it sounded self explanatory at the time.  I know exactly where the setting is and would've changed it back if I could've logged back on.  I can say one thing though, each time I reload Ubuntu, I get faster at setting it up.  It's a great OS if I can keep my fingers out of the fast moving sharp objects.

---

