---
title: "gnome and kde"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2006-12-28
what is the difference between the two???

---

### Post by kinematic on 2006-12-28
that's SOOOOOOOOOO subjective.....but in general gnome is somewhat more simplified than kde(it uses sane defaults as the devs like to say)but has a more professional look and feel(just my opinion).
kde has just about ever configuration option you can imagine and usually kde apps integrate better
but why don't you try them both and see for yourself ;)

---

### Post by jonathan.lees on 2006-12-28
Gnome is round, KDE is square.

---

### Post by BarfBag on 2006-12-28
GNOME is for people who want a simple, easy to use, desktop environment that doesn't get in the way of what you're doing.  KDE is for people who like customization and control.

---

### Post by antgul3382 on 2006-12-28
im using ubuntu amd64 now and i kinda dislike how basic the programs look in gnome. so i should use kde? that is kubuntu right? do i have to start over fresh with it or is there a way i can just "upgrade" to it??? is kubuntu tHAT MUCH MORE DIFFICULT??

---

### Post by pseudonym on 2006-12-28
> **antgul3382 said:**
> what is the difference between the two???
None. They both suck. Use Xfce! hahahahahaha

[Just kidding] :)

---

### Post by maxamillion on 2006-12-28
KDE is a desktop environment written with Qt. Gnome is a desktop environment written in GTK. Neither are difficult to use, if they were I assume less users would swear by one or the other. I prefer Xfce4 over either, but then again ... its all about choice so that's not to say any one is "better" than the other. KDE is generally the slowest because it tends to weigh heavy on resources, Gnome a little lighter, and Xfce4 even still lighter.

If you would like to install KDE with all the Kubuntu default programs (which I recommend for newer users) you can use synaptic to install the package "kubuntu-desktop" or if you prefer the command line: 
```
sudo aptitude install kubuntu-desktop
```

or

```
sudo apt-get install kubuntu-desktop
```

depending on the package manager you prefer

---

### Post by hairmetal4ever on 2006-12-28
You can install Kubuntu from within Ubuntu with those commands?

---

### Post by antgul3382 on 2006-12-28
ok people are telling me to use a lighter os  to save resources, i dont really care about that, i have a amd athlon 64 3500 with 3gb ram 512 video etc i have plenty of resources and i just dont like the programs and things that look like **** or just really basic , so kde is the one to fix that???

---

### Post by maxamillion on 2006-12-28
Yes, you can install kubuntu from within ubuntu with those commands.

I say, install both and just try them out and in the end, use what you like.

---

### Post by antgul3382 on 2006-12-28
ok ive installed it now what???

---

### Post by pseudonym on 2006-12-28
> **antgul3382 said:**
> ok people are telling me to use a lighter os  to save resources, i dont really care about that, i have a amd athlon 64 3500 with 3gb ram 512 video etc i have plenty of resources and i just dont like the programs and things that look like **** or just really basic , so kde is the one to fix that???
KDE is bigger on the eye candy if that's what you want. But it's also bigger on the unnecessary and confusing configuration options.

These days, however, any linux desktop can be made to look 'cool', provided you have the right video card and use the right window manager. Have a look at [Beryl]("https://help.ubuntu.com/community/BerylOnEdgy"), for example.

And about the use of system resources - I have a fairly new and fast machine, yet I still choose to use the 'lightweight' Xubuntu, because applications open as soon as I click the mouse. I've run Gnome on similar hardware and, while it of course works fine, it is still less responsive than Xubuntu.

---

### Post by antgul3382 on 2006-12-28
ok beryl i have to do toomuch stuff for but im trying the kubuntu now and i just restarted and the boot screen changed but nothing else is any different?????whats going on?????

---

### Post by mexlinux on 2006-12-28
> **antgul3382 said:**
> what is the difference between the two???

Lets take a sample: THE OPEN FILE WINDOW.

Attached you will see 3 windows: one from GNOME two from KDE.

The GNOME one, is the only way you can have it, there are no options from you as user to modify what you see. It makes is simple and you will get use to always have the same.

The KDE has too many options, you can see the preview in the icons (or not), you can see file permisions (or not) you can see big preview (or not), you can choose icons size, etc .... You an as a user choose how to see what you see.... Maybe a newbie too newbie might get lost.... (that's what gnome avocates say)

See the differenes?

---

### Post by pseudonym on 2006-12-28
> **mexlinux said:**
> Lets take a sample: THE OPEN FILE WINDOW.
!Exactamente! :)

---

### Post by mexlinux on 2006-12-28
> **antgul3382 said:**
> ok beryl i have to do toomuch stuff for but im trying the kubuntu now and i just restarted and the boot screen changed but nothing else is any different?????whats going on?????
At login, you must choose your session type, KDE or GNOME

---

### Post by antgul3382 on 2006-12-28
yeah thanks guys kde sux im stickin with gnome

---

### Post by hairmetal4ever on 2006-12-29
> **mexlinux said:**
> At login, you must choose your session type, KDE or GNOME

It's not doin that for me.  On boot-up the screen now says "Kubuntu" instead of Ubuntu but it still loads Ubuntu.

It asked me during installation if I wanted Ubuntu as default IIRC and I said yes, but thought I'd  still have the option.

---

### Post by mexlinux on 2007-01-23
> **mexlinux said:**
> Lets take a sample: THE OPEN FILE WINDOW.
See the differenes?

I'm quoting myself because, I finally found an explanation of why the GNOME Open file windows, is what it is.

And that explanation came from....Linus Torvalds himself!
[http://mail.gnome.org/archives/usability/2005-December/msg00022.html]("http://mail.gnome.org/archives/usability/2005-December/msg00022.html")

> 
...
That's _not_ like any other open source project I know about. Gnome seems 
to be developed by interface nazis, where consistently the excuse for not 
doign something is not "it's too complicated to do", but "it would confuse 
users".
...
Same with the file dialog. Apparently it's too "confusing" to let users 
just type the filename. So gnome forces you to do the icon selection 
thing, never mind that it's a million times slower.


---

### Post by ComplexNumber on 2007-01-23
> **mexlinux said:**
> I'm quoting myself because, I finally found an explanation of why the GNOME Open file windows, is what it is.

And that explanation came from....Linus Torvalds himself!
[http://mail.gnome.org/archives/usability/2005-December/msg00022.html](http://mail.gnome.org/archives/usability/2005-December/msg00022.html)
and what does linux torvalds know? answer: nowt about user interfaces.

---

### Post by dashnak on 2007-01-23
> **hairmetal4ever said:**
> It's not doin that for me.  On boot-up the screen now says "Kubuntu" instead of Ubuntu but it still loads Ubuntu.

It asked me during installation if I wanted Ubuntu as default IIRC and I said yes, but thought I'd  still have the option.

You still have the option, when logging in, look for a menu called "options" or something like that. There should be something like "Session". There you can choose whether to use KDE or GNOME...
The default means that the log in window is GDM or KDM, GNOME'S or KDE'S default login in window....

---

### Post by mexlinux on 2007-01-23
> **ComplexNumber said:**
> and what does linux torvalds know? answer: nowt about user interfaces.
Come on, he might not be an interface expert, but he knows -better than any of us- about computing power and options it's, which are sometimes considered "confusing" by the gnome advocates.

---

### Post by ComplexNumber on 2007-01-23
> **mexlinux said:**
> Come on, he might not be an interface expert, but he knows -better than any of us- about computing power and options it's, which are sometimes considered "confusing" by the gnome advocates.
trusting linux torvalds opinion of gnome/kde is a bit like trusting the engine manufacturer's opinion of the aesthetics and aerodynamics of ferrari car chasis'.

---

### Post by Happy_Man on 2007-01-23
Yeah, even if Linus Torvalds DID make the linux kernel, then that doesn't make him an expert on GNOME. It's like asking the programmers down at Microsoft what the plan for the Xbox 360 is. Two completely different parts of the same whole.

---

### Post by mexlinux on 2007-01-24
... beat the dealer ...

---

### Post by Lil_Eagle on 2007-01-31
> [It's] a bit like trusting the engine manufacturer's opinion of the aesthetics and aerodynamics of ferrari car chasis'

Perhaps, but what if Ferrari was right?  How dare anyone decide for me what it "too confusing".   Gnome might be simpler, but then when the average user realizes that Gnome is not the only WM,  they will mostly all agree that it's too "dumbed down".  The File and Print dialogs alone make it in my book, unusable.

Frequently when I am in a File Open dialog box, I find files that are no longer needed.  Can I delete them from there or do I have to remember the location of the files so I can navigate (with several mouse clicks) to the unwanted files and throw them in the trash.  I'd rather just delete the files directly and bypass the trash.  With KDE I can do that.

Now, let me say that there are some gnome apps that are very good, the KDE counterparts are inferior.  However, I can run them in KDE with no trouble, just like Gnome can run Amorak.  That's the beauty of open source, and if one really wanted to, they could rewrite the gnome apps to use QT instead of GTK, but in my opinion, t's not worth the effort since the cross libraries are used.

One of the reasons I switched from Windows to Linux is because I didn't like developers (and corperations) telling me what I could and couldn't do with my computer, and The Gnome Project seems to want to do just that.

---

### Post by sophwise on 2007-04-06
Hi All,

This is my first post to this forum, but have been doing Linux, *nix, *BSD for 12+years.

I have found through user feedback, and my own experiences, Gnome is good for entry-level users that are just getting started in computers in general. But any other class of user inevitably complains that its missing functionality they are used to.

The biggest rub I have found, comes when you have a Windows convert that is an "average" user that is used to the UI logic that is happening in Windows. People get used to a certain set of expected "ways" of doing things. These features aren't as much obvious things, as they are connected object logic. And its not limited to Windows.

For example, a user opens the open dialog, navigates to the target folder, and now has that "Object", the folder, in their mind. Now the thinking here is, what do I want to do in that folder. The obvious answer is that they want to OPEN a file. Thats where gnome's thinking falls short. When thinking in subliminal object logic, you expect to be able to do all the same things to that "object" as you could in a file manager, whether drag'n'drop files into it, right click to open a file in another program, etc., etc., etc.

If you type the full path of the item in the dialog, that is an object that the UI should recognize, and give you what you want.

Windows follows even more sophisticated interconnected subliminal logic, and it manages to hold a huge market share. So reducing functionality so as to not allow too many confusing options works for those users who are completely new to computers, it is a limiter to anyone else who has certain expectations of the UI.

I'm not saying this as an opinion. Nor can I say that this assessment is all inclusive of the world's population. I can say that from the MANY users I have dealt with (Windows converts and New Users alike), my statements above are entirely true and accurate. Across the board, when I run a Windows user through both Gnome and KDE, more than 90% of the time people mention something about gnome feeling too dumb (or some other similar wording). I have even had experienced users say it feels like they're back to using Windows for Workgroups with prettier graphics.

And that's not me, that is actual end users.

So, again, Gnome reducing UI functionality so as to not allow too many confusing options does nothing for helping users adopt Linux. Windows UI is more complex by far and people still manage to figure it out.
________________________________

I don't care which WM someone uses as long as it isn't explorer.exe

---

### Post by Punker on 2007-04-06
I aways liked KDE but my Kubuntu experience's did not go well so I went with Gnome and everything was fine so I got burned out on the looking at the same desktop so I installed Xfce because some apps I was useing weir from the KDE
data base so after awhile I thought what the heck I'll just install KDE 3.5 and its working good all of the desktops I went with but Gnome is my default

---

