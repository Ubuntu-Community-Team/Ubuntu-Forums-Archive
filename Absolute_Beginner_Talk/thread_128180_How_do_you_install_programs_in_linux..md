---
title: "How do you install programs in linux."
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-02-10
Is it possible for linux to have the equivalent of .exe files, where all you need is that file?  If not, what do you have to do to get your average program installed?

---

### Post by engla on 2006-02-10
It is possible [--anything is possible with linux ;-) ], but the standard way to install applications is with packets that are installed by passing lots of files to different places in your system; but, thanks to your package manager you don't have to worry about all the different files.

So, to install files, use Synaptic the package manager, or look out for stand-alone .deb (package) files.

---

### Post by karzip on 2006-02-10
[QUOTE=systemintheglitch]Is it possible for linux to have the equivalent of .exe files, where all you need is that file?  If not, what do you have to do to get your average program installed?[/QUOTE]
;) no exe's in uBz..i have a hunch that it all gets processed in the SPM.. and wish the godz of uBz will allow program access.. its seems highly monitored..we only get what they want to give..for some reasons..:D

---

### Post by Madpilot on 2006-02-10
Easiest way to isntall stuff is **Applications menu --> Add Applications**. 

The only problem with AddApp is that it doesn't have everything, just desktop stuff.

To get everything, **System menu --> Administration --> Synaptic Package Manager** and use the Search button.

In both cases, when it asks for a password, use your own user password.

There's litterally thousands of packages available thru Synaptic, so nearly everything you need should be there...

---

### Post by systemintheglitch on 2006-02-10
Im sorry.. I still don't understand.. I'm a total linux newbie... moreso than anyone on the planet!...

So could you guys explain to me about the nature of these packages, what is the need for them, how does a package manager handle this for us, what would we have to do if it didnt do it for us.. Can all programs be installed with a package manager??

These are all very important questions that i am completely confused about.. Thank you so much guys.

---

### Post by systemintheglitch on 2006-02-10
What do you mean addap doesnt have everything?? I don't get it.

---

### Post by aysiu on 2006-02-10
See the second link of my signature. It explains everything.

---

### Post by Madpilot on 2006-02-10
[QUOTE=systemintheglitch]What do you mean addap doesnt have everything?? I don't get it.[/QUOTE]

Add Applications only lists the programs that will appear in the Applications menu, so stuff like audio/video codecs, program libraries and older programs won't appear there. Also apps like the Apache web server and other things that have nothing to do with the desktop.

Synpatic, on the other hand, lists everything, including all the stuff that AddApp lists.

Basically, these apps get packages from online repositories run by Ubuntu - so you do need a working net connection for them to function.

Have a look at [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto) and [http://wiki.ubuntu.com/AddingRepositoriesHowto](http://wiki.ubuntu.com/AddingRepositoriesHowto) for more info.

---

