---
title: "Uninstalling Software"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by islander_810 on 2007-02-16
Dejvid's post reminded me of a problem i've been facing - uninstalling software. I'm new to Linux, and i've been unable to uninstall everything i've installed. 
What i mean is the applications that i installed using apt-get can be easily removed. But what about those in which i use ./configure to install them. Will merely deleting the folders where they are installed suffice?

---

### Post by true_friend on 2007-02-16
Usuallay there is a script called uninstall u can run it from same directory by ./uninstall
i think it should solve problem.
Regards
True_Friend

---

### Post by nhandler on 2007-02-16
If the script has a special method of being removed, it is more than likely mentioned either in a readme/faq, or on their website.

---

### Post by islander_810 on 2007-02-17
well, what if there's no uninstall script.

For eg, i have lynx source, but no uninstall script. i know that i can well install/uninstall from synaptic package manager, but i just mentioned it as an eg.

So, isn't there any straight-forward method like
apt-get remove or Add/Remove Programs?

And what abt deb packages? Are the entries added to synaptic package manager or Add/remove programs once i install them?

---

### Post by 3rdalbum on 2007-02-17
In a terminal, go to the directory that contains the source code.

The command is one of these two following lines:

sudo make uninstall
sudo make remove

(I forget which)

Then try:

sudo make clean

---

### Post by mcduck on 2007-02-17
When compiling software yourself I recommend using checkinstall. ('sudo apt-get install checkinstall', and when compiling use 'sudo checkinstall' instead of 'sudo make install').

Checkinstall creates a .deb package and then installs that, so compiled programs will show in Synaptic and can be easily removed using apt-get or Synaptic.

---

### Post by A_mu on 2007-02-19
The situation is that I had deleted the directory contains the source files. that way, how can I uninstall the software?

---

### Post by Spr0k3t on 2007-02-19
I had a similar situation as yours.  What I had to do is download and unpack the sources.  Once there, i was able to do the ./configure to create the uninstall.  Mcduck has it dead on with the creation of the deb packages.  It makes for a much easier uninstall later on.  I created a deb for weechat 0.2.3 using this method.  So when doing a sudo make install, perform the checkisntall instead.

On another note, there's a method to use --purge with apt-get, but I haven't worked with that one yet, just a thought.

---

### Post by mcduck on 2007-02-19
> **Spr0k3t said:**
> 
On another note, there's a method to use --purge with apt-get, but I haven't worked with that one yet, just a thought.
That still only works for applications installed with package management (.deb packages), not for stuff installed from source. Apt-get doesn't even know that the app exists in your system if it wasn't installed with package management..

---

### Post by Spr0k3t on 2007-02-19
Yeah, I figured it would.  But that would be an option once the deb package has been created and installed.

---

### Post by boyzuo on 2007-02-19
> **A_mu said:**
> The situation is that I had deleted the directory contains the source files. that way, how can I uninstall the software?

same situation as I am...........

---

### Post by mcduck on 2007-02-19
then you'll just have to get the sources back so that you can use the uninstall script that (hopefully) came with them :)

---

