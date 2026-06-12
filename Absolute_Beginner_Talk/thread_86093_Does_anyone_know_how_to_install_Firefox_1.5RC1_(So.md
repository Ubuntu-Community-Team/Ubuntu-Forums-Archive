---
title: "Does anyone know how to install Firefox 1.5RC1? (Solved)"
date: 2005-11-04
forum: Absolute Beginner Talk
---

### Post by Animus on 2005-11-04
I uninstalled the old firefox, as I'd installed Opera, and was tired by Firefox's memory leaks and otherwise shoddy workmanship, however I miss my theme and my widgets too much, and as it turns out I'm not that big of a fan of opera.  I was wondering if anyone knew how to install ForefoxRC1, I tried using the Beta2 installation intructions, but it wouldn't work.  Any ideas?

---

### Post by Kapre on 2005-11-04
[QUOTE=Animus]I uninstalled the old firefox, as I'd installed Opera, and was tired by Firefox's memory leaks and otherwise shoddy workmanship, however I miss my theme and my widgets too much, and as it turns out I'm not that big of a fan of opera.  I was wondering if anyone knew how to install ForefoxRC1, I tried using the Beta2 installation intructions, but it wouldn't work.  Any ideas?[/QUOTE]

Animus - maybe this [thread]("http://www.ubuntuforums.org/showthread.php?t=79283&highlight=firefox+1.5") would be of interest to you. Also, you can try Epiphany Web Browser (which I think you'll also like because it has the look and feel of Firefox).

K

---

### Post by Animus on 2005-11-04
I installed FireFox RC1, but how do I make icons for it?  I deleted the old icons when I uninstalled the previous firefox, and I can't seem to find a way to make any for this one...

Also, does anyone know if it matters that this is the i686 version of firefox, and I'm using a K7 kernal?  I couldn't see a way to get a K7 version, so I just stuck with this...

---

### Post by Animus on 2005-11-04
-bump-

---

### Post by Animus on 2005-11-04
anyone?

---

### Post by aysiu on 2005-11-04
First of all, have patience. You don't have to keep bumping your thread and say "anyone?" Three hours may seem a long time to you, but everyone here is a volunteer and the people will help when they get a chance. We're all just other users like you.

[QUOTE=Animus]I installed FireFox RC1, but how do I make icons for it?  I deleted the old icons when I uninstalled the previous firefox, and I can't seem to find a way to make any for this one...[/quote] What do you mean by "make icons"? Are you talking about creating a launcher? Are you trying to create your own icons through GIMP or Inkscape?

> 
Also, does anyone know if it matters that this is the i686 version of firefox, and I'm using a K7 kernal?  I couldn't see a way to get a K7 version, so I just stuck with this... What do you mean--"if it matters"? As far as I can tell, it's either working or it isn't.

---

### Post by Animus on 2005-11-04
By Icon, I mean the icon to click to activate the program, so maybe "launcher" is the right word, frankly I don't know.

I was wondering if the kernal you're using will affect the programs performance.  If there were a version of Mozilla optimized for the K7 kernal, or if using the i686 version was more unstable than another version, etc.  

The only reason I bump is when the page leaves the first page, and the question isn't answered.  Its frustrating to see your question fade into obscurity without so much as an "I don't know"  from someone, but I'll stop if it upsets people.

---

### Post by aysiu on 2005-11-04
[QUOTE=Animus]By Icon, I mean the icon to click to activate the program, so maybe "launcher" is the right word, frankly I don't know.[/quote] Yeah, you're looking for a launcher. Just right-click on the panel and select "Add to Panel" and "Custom Applications Launcher." 

For command, find the exact location of your new Firefox installation and type that in. For example, if you put your new Firefox 1.5 in your home directory, the command would be /home/animus/firefox/firefox

The icon (using the above assumption about location) would be in /home/animus/firefox/icons/firefox.png

> 
I was wondering if the kernal you're using will affect the programs performance.  If there were a version of Mozilla optimized for the K7 kernal, or if using the i686 version was more unstable than another version, etc. Hm. No idea.

> 
The only reason I bump is when the page leaves the first page, and the question isn't answered.  Its frustrating to see your question fade into obscurity without so much as an "I don't know"  from someone, but I'll stop if it upsets people. No, it's fine. I'm just saying that three hours is too little to wait. Some people (unlike myself) check these forums only one time a day--they may sweep through all their unread threads at that time. I'd say give it at least a day before bumping it.

---

### Post by Animus on 2005-11-04
Ahh, but I don't necessarily want to add it to the panel, I'd prefer it be under "internet" or whatever.  However, when I browse for the installation which is in the Opt folder in the file system, I can't seem to select that. I tried /filesystem/opt/firefox, but got an error, not sure why though.  I know the program works, because I'm using it right now, I just can't make an icon for it.  

I'll wait at least a day henceforth before bumping.

---

### Post by aysiu on 2005-11-04
Are you using SMEG to add it to the applications menu? What error do you get?

---

### Post by bored2k on 2005-11-04
```
 sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
```
 ```
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```Use the default Firefox icon afterwards.

---

### Post by Animus on 2005-11-04
I entered that into the terminal, and everything seemed to go fine, except that I still have no firefox icons.

I'm not using any tools, as I have no idea what to do...this isn't really the kind of problem i've run into before.

There is just no icon for starting firefox, and I have no idea what to do to make such an icon appear...

---

### Post by aysiu on 2005-11-04
Can you attach a small screenshot of what your icon-less Firefox launcher looks like?

---

### Post by Animus on 2005-11-04
I don't have a launcher though, at least I think I don't.  There is nothing to click on to open firefox.  No icon, no launcher, nothing.  In order to open firefox, I have to type firefox in the terminal everytime, and leave the terminal running.

---

### Post by aysiu on 2005-11-04
Under Applications > System Tools, there should be something like Menu Editor or Application Menu Editor. This program is also known as SMEG. What happens when you click on that?

---

### Post by Animus on 2005-11-04
It opens up, and shows me the programs installed in my computer, and the icons under Internet, graphics, sound and video, etc.

---

### Post by aysiu on 2005-11-04
Okay. There should be two sides to this new menu.
On the left side, click on Internet.
The right side should pop up with your list of internet applications.
You can either modify the Firefox entry that came with your default Gnome installation *or* you can add a new menu entry. I'm not sure what the exact steps are (I'm in KDE right now), but some kind of right-clicking should allow you to edit the Properties of an existing entry or add a new entry.

---

### Post by bored2k on 2005-11-04
There's really no way to make a mistake using SMEG, but here's another way: if the firefox RC dir is in opt, I am sure ```
sudo mv /usr/bin/firefox /usr/bin/firefox2
```
```
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
``` will work. This will load the RC everytime FF is invoked.

---

### Post by Animus on 2005-11-04
I don't think you understand my problem though, I can't find a way to invoke FF, because their is no icon/launcher/whatever for it, at all.  Firefox was taken off my computer, I installed the RC, and now can't find a way to launch it other than the terminal.  

aysiu-Yes, however I can't figure out how to add firefox, as when I try it doesn't seem to work...what exactly do I try to load to it?  is their a specific file in the installation I need to use?  There is no file on this computer to open firefox, save through the terminal

---

### Post by aysiu on 2005-11-04
I don't think you understand the solution to your problem.
You **create** the launcher.
You create it. It doesn't exist already. You make it happen.
Okay. You made me log out of KDE and log into Gnome, so please pay attention (I'm even including screenshots):

1. [Go to Applications > System Tools > Applications Menu Editor](http://i22.photobucket.com/albums/b337/psychocats/3a2c0257.png)

2. Click on Internet. Then [From File, select New Entry](http://i22.photobucket.com/albums/b337/psychocats/ace31575.png)

3. For the new entry [Make Firefox the **Name** and put whatever you would ordinarily put into terminal to launch Firefox as the **Command**](http://i22.photobucket.com/albums/b337/psychocats/e9e19907.png)

4. If you want, click on the part that says **No Icon** and select an icon to make your Firefox icon.

From now on, it'll be in your Applications menu under Internet.

Let me reiterate. If you usually type ```
/opt/firefox/firefox
``` to launch it from the terminal, put ```
/opt/firefox/firefox
``` as the **Command** in your new entry. If you usually type ```
firefox
``` to launch it from the terminal, put ```
firefox
``` as the **Command** in your new entry.

---

### Post by Animus on 2005-11-04
Aha, that got it, thanks for the help.

---

### Post by aysiu on 2005-11-04
[QUOTE=Animus]Aha, that got it, thanks for the help.[/QUOTE] Glad it finally worked out!

---

