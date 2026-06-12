---
title: "GTK and realtek driver problem--Don't want to get rid of ubuntu."
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by mrshmizzie on 2008-03-19
I've looked around the internet and forums for an answer to this one, but to no avail. Similar but not any help. I recently installed ubuntu because I have gotten sick of windows and wanted something new.

My computer is an acer aspire 7520-5071 running vista. I managed to install both my wireless adapter and graphics card. I installed the drivers from the realtek website for the sound and restarted as per the instructions. Once I restarted though I received the following error:

Your session only lasted less than 10 seconds. If you have not logged out yourself, this would mean that there is some installation problem or that you maybe out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

(Process: 5684) GTK-warning ** This process is currently running setuid or setgid. This is not a supported use of GTK+. You must create a helper program instead. For further details, see:

[http://www.gtk.org/setguid.html](http://www.gtk.org/setguid.html)

Refusing to initialize GTK+.

(Process: 5688) GTK-warning ** This process is currently running setuid or setgid. This is not a supported use of GTK+. You must create a helper program instead. For further details, see:

[http://www.gtk.org/setguid.html](http://www.gtk.org/setguid.html)

Refusing to initialize GTK+.

/etc/gdm/xsession: beginning session setup...
x-session-manager: error while loading shared libraries:libasound.so.2: cannot open shared object file: no such file or directory.

I can't get past this. I tried the different failsafe sessions, but haven't been able to log into the GUI. I can get into a terminal, but because I don't know much about using it, it's pretty much worthless to me. 

I really don't want to do a new install, because of the pain it was to get the wireless and graphics card to work. I will if I absolutely have to, but I also am not sure how to do that properly. ie erasing the previous and then reinstalling without messing up the boot. 

Any help would be greatly appreciated. 

Hopeless,

-Mrshmizzie

---

### Post by Suparious on 2008-03-19
Well, not sure that your Realtek driver problems are related to the GTK, unless there was a problem with whatever method was used to install that driver.

From the below error, it would seem that your ALSA libraries are missing.

try:

```
sudo apt-get install libasound2 
```

or:

```
sudo dpkg-reconfigure libasound2 gdm
```

When I do the second option myself, I get a "You may need to execute the asoundconf(1) set-default-card macro."

running "asoundconf" by itself should display something with "asoundconf is-active".

---

### Post by mrshmizzie on 2008-03-21
Well what I did was download the drivers from the realtek website. Untarred it along with all the other tarred folders inside it. Then I clicked on install wich brought up another box with three options and I clicked run in terminal. It scrolled through some stuff then I restarted. Once I restarted it then I got the above errors, not quite sure what I did wrong. Once I get back to my comp. I'll try your suggestions. Thanks. I'll post what happens.

---

### Post by jimv on 2008-03-21
I have no clue about how to fix your current issue, but if you end up having to reinstall, don't use hte linux drivers from the realtek site.  Get NdisWrapper (i think it's in the repos, or you can get it off sourceforge)

Once you have that installed, you can then use your Windows wireless drivers for your network card.  I have a Realtek wireless card and Ndiswrapper was the only thing I could get to work.

To use Ndiswrapper, you need a copy of your Windows wireless driver.  In partifular the INF and SYS file for it.

Once you have that, just type this in a command line:

[INDENT]sudo ndiswrapper -i whateveryourdriveris.inf
sudo ndiswrapper -m
sudo ndiswrapper -ma
sudo ndiswrapper -mi
sudo modprobe ndiswrapper[/INDENT]

At this point your wireless should be up and running.

---

### Post by mrshmizzie on 2008-03-21
Thanks for the reply.

It wasn't my wifi that I couldn't get to work. Well at first it was! It's the sound that I completely screwed up my computer with. I'll do a clean install, but I really don't want to.

---

### Post by asmoore82 on 2008-03-21
did the sound work at all before you tried to install something from realtek?

---

### Post by mrshmizzie on 2008-03-24
The sound never worked in ubuntu. It did however work in vista.

---

