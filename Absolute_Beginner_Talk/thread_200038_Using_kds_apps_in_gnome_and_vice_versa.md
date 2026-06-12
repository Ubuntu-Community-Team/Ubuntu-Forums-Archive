---
title: "Using kds apps in gnome and vice versa"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by bohboh on 2006-06-19
Is it ok to use kde apps in gnome and vice versa?

I have asked questions regarding certain apps and the response i get is "if you use gnome then this app is the best, for kde its that". Does it matter? They seem to all work ok.

In what way are gnome, kde, etc different for them to have there own apps?

---

### Post by Kilz on 2006-06-19
[QUOTE=bohboh]Is it ok to use kde apps in gnome and vice versa?

I have asked questions regarding certain apps and the response i get is "if you use gnome then this app is the best, for kde its that". Does it matter? They seem to all work ok.

In what way are gnome, kde, etc different for them to have there own apps?[/QUOTE]
Yes kde apps will work in gnome, Im sure gnome apps will work in kde. I use the k3b cd burining application in gnome all the time. What you may find is some things may not look as pretty, or they dont match the rest of the applications you use. But they will function. 
The big diffrence in kde and gmome is the toolkit they use to make the widgets. Qt for kde and gtk for gnome. At one time the toolkit for kde wasnt free, to my knowlage it still isnt if you want to use it to design a commercial application.

---

### Post by steve.horsley on 2006-06-19
As you noticed, they all work. Gnome apps are designed to adopt the gnome look and feel, use the gnome theme fonts etc. Same for KDE apps using the KDE L&F. So gnome apps in KDE look "different" and vice versa.

Another issue is that running a gnome app in a KDE desktop or vice versa loads a lot of extra support libraries, so the first foreign app you load takes a long time to load up, and tends to eat a lot of memory.

I tend to stick with apps for the same desktop just for the L&F consistency, but hell, if the opposition has a better app for my needs, I'll use it. I guess many people will have apps  from both sides of the fence in their favourites liet.

---

### Post by bruce89 on 2006-06-19
[QUOTE=steve.horsley]As you noticed, they all work. Gnome apps are designed to adopt the gnome look and feel, use the gnome theme fonts etc. Same for KDE apps using the KDE L&F. So gnome apps in KDE look "different" and vice versa.
[/QUOTE]
Not as such, there is a special theme in Kubuntu which uses QT to draw GTK+ widgets.

---

### Post by bohboh on 2006-06-19
So i can install kde using apt-get, so why bother with seperate distro's for kde and gnome, and instead select the session from the login screen. Or am i missing something.

---

### Post by dlai on 2006-06-19
As I have understood the KDE runs on what is called Qt libraries/engine (i do not know) and GNOME use GTK. Since all of KDE use the Qt, the apps made for KDE also do that, and if KDE is already using Qt when started, it is not as demanding to run the apps made on Qt, but with GTK/GNOME apps you would have to run the GTK libraries/engine besides the Qt. So I would think it is a performance issue, and as well a compability issue, since some of the Qt apps for example use some part-apps (which are apps run inside others, for example if you need a browser or a pdf viewer inside an app) these usually follow with KDE when you install it. If you install a KDE app in GNOME that need on of these parts it usually won't install it with them. Moreover the GNOME apps look better in GNOME and the KDE better in KDE. Systray integration usually work better as well. Integration in general work better.:rolleyes: Oops  a little slow i see. But I hope it provides some clarification, if i got it right at least

---

### Post by bohboh on 2006-06-19
Is the performance hit enough to warrant not using kde in gnome and vice versa, or is that dependant on the app and its function, i.e. video/photo editing compared to text file editing.

---

### Post by aysiu on 2006-06-19
For some people, it's a bandwidth (dial-up) or space (no room on the hard drive) issue, since the first KDE application you install in Gnome or vice versa will bring a whole slew of libraries with it.

Non-native applications take a little longer to load, and sometimes drag-and-drop will move files instead of copying them.

And... they may not look that well integrated into the rest of your desktop.

Otherwise, there's no problem with using non-native applications.

---

### Post by bruce89 on 2006-06-19
It will run at the same speed, provided you have enough memory to have all the GNOME librarys and all the KDE ones running at any one time.

---

### Post by bohboh on 2006-06-19
So i installed kde using this tut (i think it was this one) [http://www.psychocats.net/ubuntu/kde.html]("http://www.psychocats.net/ubuntu/kde.html")

So does that mean that i have kde installed and when logged in under "session kde" all my native kde apps will run more efficiently than in gnome? By following that tut is my installation effectively kubuntu?

Also, i am curious, how would i go about monitoring resource consumption when running native and non native apps?

---

### Post by aysiu on 2006-06-19
Having both installed doesn't make a non-native application load up any more quickly.

**Installed** just means it's on your hard drive.

If it's **running** in its native environment, it'll look integrated, load up more quickly, and behave exactly as it's supposed to.

Right now, for example, I have Xubuntu, Ubuntu, and Kubuntu all installed on the same partition. I have a ton of KDE, XFCE, and Gnome applications **installed**.

But right now I'm logged into Gnome, so if I load up Kolourpaint (a KDE application), it takes a bit longer to load.
If I log out of Gnome and log into KDE, Kolourpaint will load up almost immediately. In both cases, Kolourpaint **installed**, but how quickly it loads depends on what desktop environment I'm **using**.

---

### Post by bohboh on 2006-06-19
So having installed kde and logged in to the kde session, that effectively is kubuntu?

Just trying to work out why there are two distros, ubuntu and kubuntu.

---

### Post by aysiu on 2006-06-19
There's only one distro.
Ubuntu is Ubuntu with a Gnome desktop.
Kubuntu is Ubuntu with a KDE desktop.
Xubuntu is Ubuntu with an XFCE desktop.

If I install Ubuntu and then add Kubuntu and Xubuntu, I didn't just install three operating systems. I installed one operating system and added two desktop environments.

---

### Post by bohboh on 2006-06-19
I seeeee, its all starting to fall into place! :D 

Well thats cleared something up which i didnt realise until recently how little of it i understood. :)

I have never learnt as much as i have done in such a short space of time. Only installed ubuntu a week ago, havent looked back. 

Only wish i could reclaim my hd space and remove xp altogether, but i do a lot of video editing and have my "process" in place for trasnferring video from my digicam to dvd using freeware tools and unfortunately there arent any linux equivalents, (well i havent found any yet).

Thanks everyone, (all i ever seem to do in this forum is thank people)

=D>

---

### Post by aysiu on 2006-06-19
[QUOTE=bohboh]
I have never learnt as much as i have done in such a short space of time.[/QUOTE] That's how I feel, too. I've been using Ubuntu for a year now, and it feels as if I've always used it...

---

### Post by steveneddy on 2006-06-19
aysiu is so **smart**
Many good advice posts and threads by aysui. I also run many different DE's and enjoy them all. 

-SE

---

