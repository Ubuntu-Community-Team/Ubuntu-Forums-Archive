---
title: "How do i install this??"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by SniperKIng on 2007-04-02
Ok im very new to this Ubuntu and at the moment i dont even know how to get files to run.OK i just downloaded an playstation 2 emulator to play my ps2 games on the pc but i dont know how to use it lol ???

The latest release of the program luckily for me is linux based and came out 2 days ago.

I will post a link to the download its only about a 20 second download. and can some one look at it and tell me how to get it open lol.i can see the app there but clicking it does nothing on my michine.

Here is the download :- [http://www.pcsx2.net/files/8019](http://www.pcsx2.net/files/8019)

---

### Post by 1/0 on 2007-04-02
I don't know anything about playstation but I found this link:

[http://doc.gwos.org/index.php/Playstation_Emulator](http://doc.gwos.org/index.php/Playstation_Emulator)

Maybe it'll help?

---

### Post by theicyj on 2007-04-02
Try searching Synaptic, I think there is a playstation emulator in the repositories.  That would probably be much easier to install.

---

### Post by finferflu on 2007-04-02
I've just found this on the home page of that website:
> 
It took only a couple of hours to convince us that it is impossible to make a Linux release without also releasing the source. For those people that had problems with the binaries, they can now go to the sourceforge site and compile their own executables! Hopefully this will resolve all the random crashes and exceptions. Note that the Cg Toolkit
is required for successful compilation. To compile everything type

> sh build.sh all

---

### Post by r4ik on 2007-04-02
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

Good luck !

---

### Post by SniperKIng on 2007-04-02
> **finferflu said:**
> I've just found this on the home page of that website

It took only a couple of hours to convince us that it is impossible to make a Linux release without also releasing the source. For those people that had problems with the binaries, they can now go to the sourceforge site and compile their own executables! Hopefully this will resolve all the random crashes and exceptions. Note that the Cg Toolkit
is required for successful compilation. To compile everything type:



lol that doesnt mean nothing to me but thanks for trying.

Thanks for all the replies everyone but i just dont think ubuntu is really for me lol but ill try it out for a few more hours

---

### Post by finferflu on 2007-04-02
> **SniperKIng said:**
> lol that doesnt mean nothing to me but thanks for trying.

Thanks for all the replies everyone but i just dont think ubuntu is really for me lol but ill try it out for a few more hours
ok sorry, I'll make it clearer:

you need to run that command from inside the application folder. So, let's suppose you have downloaded and unzipped (or untarred) the package on your Desktop, in a terminal you should type:

```
cd Desktop/<name of the folder>
```

cd means "change directory", so after the command cd you have to type the path were the extracted folder is.

Then type the command written in the previous post:

```
sh build.sh all
```

Hope it's clearer now. It's not difficult, it's just very different from what you're used to, but once you get the grip, you'll see what I mean.
If you need further help, just ask ;)

---

