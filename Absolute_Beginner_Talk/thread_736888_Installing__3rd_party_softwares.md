---
title: "Installing  3rd party softwares"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Snitz on 2008-03-27
I'm finally on Ubuntu 7.10 Gust Gibbon and I need to know how can I start installing 3rd party softwares such as Amsn and Xmms?

Thanks.

---

### Post by Ub1476 on 2008-03-27
I believe both Amsn and XMMS can be found in the repos. Note that Amsn is written in QT (KDE) and XMMS is written in GTK1, so they both look plain ugly on Gnome/Ubuntu.. Emesene is a nice GTK (Gnome) app for IM and Audacious is a good nautilus replacement (written in GTK2).

If interface doesn't worry you, it doesn't matter of course:)

---

### Post by kesman on 2008-03-27
First go to system -> administration -> software sources and enable extra repositories.
Second, go to [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method_for_Adding_Repositories](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method_for_Adding_Repositories) and add the medibuntu repository to your sources.list, it's the bottom one in the example sources.list.
Third, open up terminal and run the following commands to update your software sources:
```

sudo apt-get update

```
and then go to applications -> add/remove applications and set it to search "all available packages" and search for the application you want.

---

### Post by oedha on 2008-03-27
i delete the content since....read my edit message :)

---

### Post by Snitz on 2008-03-27
I got this error while adding the medibuntu repos.

> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by kesman on 2008-03-27
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

Did you notice that part too?

---

### Post by Snitz on 2008-03-27
Yes, but bare with me, I'm still new to all of this, what should I do with it?

---

### Post by kesman on 2008-03-27
Run it in terminal.

---

### Post by Snitz on 2008-03-27
I did, and it said "OK".

---

### Post by kesman on 2008-03-27
Now run 
```

sudo apt-get update

```
in terminal too, and if it doesn't give you any errors, close terminal, open up add/remove applications and search for xmms.

---

### Post by Snitz on 2008-03-27
Ah yea, it found them.
Now just a question, would Amsn and Xmms work on Gnome/Ubuntu?

---

### Post by kesman on 2008-03-27
Yes, any application you find from add/remove will definately work.

---

### Post by Snitz on 2008-03-27
AH, thank you man for your help. I appreciate it.
I feel so home using Ubuntu.
Thank you again.

Just a quick question, where can I find the "Network Manager" ? I can't seem to locate it.

---

### Post by kesman on 2008-03-27
It's the two computer screens in the top right corner, doubleclick on it to open network manager.

---

### Post by Snitz on 2008-03-27
Weird, I don't have a "2 computer screens" in the top right corner :\

---

### Post by kesman on 2008-03-27
Then I'm not sure. If you have a wired network connection, you should have the icon there somewhere. Otherwise, I think you can find it from system menu somewhere.

---

### Post by Snitz on 2008-03-27
This is what I did, right click on taskbar >> add to panel >> network monitor

It now shows 2 monitors and when I double click them, it shows me my wired and wireless networks but the question is how do I create and launch a pppoe connection when I'm at home.

At work I use a wireless internet and at home I use a pppoe connection.

---

### Post by linuxtoindia on 2008-03-27
try to install it by terminal automatically


''sudo apt-get and all that stuff,, and then install the ffmpeg plugins!

---

### Post by kesman on 2008-03-27
> **linuxtoindia said:**
> try to install it by terminal automatically


''sudo apt-get and all that stuff,, and then install the ffmpeg plugins!

What are you talking about?

---

