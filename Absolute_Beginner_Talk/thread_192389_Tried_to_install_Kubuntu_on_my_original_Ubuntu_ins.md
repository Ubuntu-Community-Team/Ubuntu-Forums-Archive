---
title: "Tried to install Kubuntu on my original Ubuntu install..."
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by roncg41677 on 2006-06-08
...according to http:[http://doc.gwos.org/index.php/BreezyCust]("http://doc.gwos.org/index.php/BreezyCust"). My machine hung up at the very end of the Kubuntu Desktop install, where the terminal says it is setting up the Kubuntu desktop. It was completely frozen, so I had to hard reboot. Needless to say that botched things up. Oh, and I had selected KDE as my default DM during the install. Now, I get the KDE boot screen, but it still boots into Gnome (?). I'm baffled. I tried to uninstall KDE in Synaptic, and that messed things up further, so I reinstalled it, and I'm back where I was.

I wanted to be able to try both environments for a while and find out which I really liked for day to day use. Now, I know I have KDE somewhere on my computer, but I have no idea how to boot into it. Please help.

---

### Post by NoUse on 2006-06-08
You don't need to install kubuntu seperately.  From inside ubuntu just run:
sudo aptitude install kubuntu-desktop

Then you can select a KDE session from the login screen.

---

### Post by aysiu on 2006-06-08
It's two commands, actually: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` For more details: [http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

### Post by taurus on 2006-06-08
It doesn't matter which GUI you use, GDM or KDM, you can pick which window manager you want to use before you enter your username and password.  Look at the bottom left corner for some option.  And the reason it logs you into Gnome because you have that as your default so if you don't pick any window manager, it will use the default one which is for you is Gnome then...

---

### Post by roncg41677 on 2006-06-08
Sorry, I wrote my original post in a hurry, and maybe didn't include enough detail. 

I used Synaptic, and marked "Kubuntu Desktop" for install. It took over an hour (on my 256kbps DSL connection) to download 150 packages. It included Amarok and a bunch of other Kubuntu apps. After the download and during the install there was a drop down box for me to select my default environment, "GDM" or "KDM". I selected "KDM". It continued to install, and then hung up on the very last step. So after waiting 20 minutes I shut off the computer with the power switch and rebooted. I saw the shell scrolling and a line went by that said something to the effect of "Gnome is not your default environment" or something, and then some KDE scripts started scrolling. The KDE login screen appeared with the blue "Kubuntu" wallpaper. I put in my user name and password and the Gnome splash thing came on that says "Loading Nautilus" etc., then it boots into Gnome. I had chosen KDE as my default. I'm really confused.

At the KDE login screen (at least I'm assuming that's what it was) there are 3 buttons for "menu", "session" and one other thing (this is on my work computer and I'm at home right now, so I can't look). Do I need to select one of those? I assumed KDE would load automatically since I had chosen it as my default.

I really appreciate all of the help. You guys are helping me on my bumpy road to learning Linux, and I AM loving it :D .

---

### Post by aysiu on 2006-06-08
KDM and KDE are not the same thing.

KDM is the "display manager." For most intents and purposes, it just handles the login screen.

KDE is the actual "desktop environment" where you do stuff after you've logged in.

Making KDM the default does not make KDE the default. KDM provides you with the login screen, but you can still log into Gnome.

The **Session** button lets you switch between Gnome and KDE.

---

### Post by roncg41677 on 2006-06-09
Genius!!!!! Thank you aysiu!

---

### Post by roncg41677 on 2006-06-09
Yep, that was it! I'm typing this from my KDE destop right now. I had been using Gnome for a couple of weeks on Ubuntu, and I think it really grew on me, but I will give KDE a shot for a while. 

If I decide that I want to go back to Gnome for good, should I uninstall KDE, or just leave it on? Also, what packages would I need to remove to uninstall it?

---

### Post by aysiu on 2006-06-09
I wouldn't uninstall KDE unless you're hard up for hard drive space. It really doesn't take up that much room, honestly.

If you installed KDE using the method I recommended, then you can remove it by typing ```
sudo aptitude remove kubuntu-desktop
``` If you didn't, you can use this page: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by FyreBrand on 2006-06-09
I've been thinking about installing KDE because some of the programs I want to use say "intended for KDE".  Can I install them in the Gnome desktop environment and use them, or do I have to use KDE?  It is just a few programming tools/IDE's that I want to use.

If I install KDE can I still use the apps I installed under Gnome (like eclipse) or do I have to reinstall them under KDE.

I apologize for such basic questions, but I don't quite understand the effective difference between Gnome and KDE yet.

---

### Post by roncg41677 on 2006-06-09
I love this!! I had no idea I could have 2 different desktop environments on one distro! I love being able to switch back and forth and try them both out. I wonder if I could add XFCE too? I'll have to check that out. So far though, I still love Gnome.

Fyrebrand, I just tried loading up Konqueror and Kaffeine in Gnome and they both seem to run fine. When I installed the Kubuntu desktop it made all of the KDE apps available, so I have all of the Gnome and KDE apps available in both environments. Pretty sweet \\:D/  .

---

### Post by aysiu on 2006-06-09
Sure, you can add XFCE, too. I have.
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by FyreBrand on 2006-06-09
roncg41677 ~ Thanks.  I think I will just install the KDE since I have plenty of room.  This will give me a chance to learn what each are about.  The learning curve is a little steep but fairly friendly at the same time.  Thanks for the feedback.

ps: i am using the two step instructions you posted aysiu.  it's working great. :)

---

### Post by roncg41677 on 2006-06-09
Thanks again aysiu! Could I also just mark the Xubuntu Desktop for install like I did with the Kubuntu desktop in Synaptic?

Fyrebrand, just be sure to install the **Kubuntu** desktop and not the **KDE**. I know it's a little confusing, but as far as I know this is necessary.

I'm also learning about Linux (although maybe a few months ahead of you). One really good resource I have found is a podcast called [Linux Reality]("http://www.linuxreality.com/"). The host explains Linux from the very beginning. Each show is around 30 minutes, and focuses on one topic like distros, the file system hierarchy, or command line basics. I highly recommend it. If you don't have an mp3 player you can just download them and listen to them on your computer.

Also scour this board, the wiki and the howto's as much as possible. Have fun!

---

### Post by aysiu on 2006-06-09
[QUOTE=roncg41677]Thanks again aysiu! Could I also just mark the Xubuntu Desktop for install like I did with the Kubuntu desktop in Synaptic?[/QUOTE] You could, but then if you wanted to remove Xubuntu later, it might not be as easy.

---

### Post by roncg41677 on 2006-06-09
Wow, you are *fast*.:D

---

### Post by FyreBrand on 2006-06-09
The install has gone great.  I did the install kubuntu-desktop like aysiu explained.

i am at the postfix configuration and it i am not sure what to tell it. the options are:
1. no configuration
2. internet site
3. internet with smarthost
4. satellite system
5. local only.

i'm not really sure what it's requesting.  i am on a home network with my wife's computer.  we connect to a dsl connection through a residential gateway-router.  what do i answer it?

---

