---
title: "I'm in at the deep end"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by *desk* on 2006-02-05
Hi All

Took me quite a while to find the New Thread icon.

I've used Windows for a fair amount of years, Windows 95 and even version 3.11.
Yesterday I decided to turn over a new leaf, and jump blindfold into Linux.

I found Ubuntu by chance, wiped XP and installed with no problems apart from not recognising my SoundBlaster and Lexmark printer.

The Distro is working very well but I just don't know how to run an application once I download it..... In Windows I just double click. There are DEB and RPM and even TGZ folders which I can unzip but get no further.  There must be a simple answer but I'm too Windows orientated to find it......otherwise I think I am going to enjoy this new experience but I think I will be knocking on your door a fair amount.

Des Kinsman

---

### Post by Perfect Storm on 2006-02-05
Most application/programs can you get through synaptic package manager (system tab ---> Adminstration ---> synaptic package manager) or use apt-get in the terminal (Application tab ---> accessories ---> terminal).

But first you might set up your sourcelist so ubuntu get access to alot more software. Open the terminal and write:

```
sudo gedit /etc/apt/sources.list
```

You now see alot of lines. Remove the **#** infront of the lines (except where there's two of them in a row)

also add:

[b]## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./
[/b]

save the sourcelist.

write in the terminal:
```
sudo apt-get update
```

Now things will be up to date and you'll have more than 18000 stuff avaible to download very easy. Go to synaptic package manager and use the search button to seek for what you're looking for.

---

### Post by Stealth on 2006-02-05
Well, what you can do is fire up a terminal (Programs -> Accessories iirc) and:

If you have a DEB type: "sudo dpkg -i nameofdebfile.deb"

If you have an RPM you can try: "sudo alien nameofrpmfile.rpm" and then try the above command with the newly generated deb

And for Tar.Gz/Bz2 (which are usally source codes needing compiling, you should try searching the package in Synaptic first) check [this out!](http://www.tuxfiles.org/linuxhelp/softinstall.html)

Synaptic (in System -> Administration) is your program for finding and installing other programs. Just search for whatever you want, select it, and it'll download it, any dependencies, and install it for you :)

---

### Post by cdhotfire on 2006-02-05
Hello. :)

For debs do, in terminal, Applications -> Accessories -> Terminal
```

$ sudo dpkg -i package.deb

```

Bam its installed.

For rpm, their actually meant for another distro so only sometimes we can use them. So we do
```

$ sudo apt-get install alien
$ sudo alien package.rpm
$ sudo dpkg -i newpackage.deb

```

Bam its installed, but these usually don't come out with icons in Application menu, so you can probably add them with Applications -> System Tools -> Application Menu Editor.  Usually the command is the name of the package, ex. Firefox is just firefox.

For the other ones like tgz and bz2. Its a little harder, here i go. First you must unpack it and "cd" to the folder it is at.
```

$ cd nameoffolder
$ sudo apt-get install build-essential dh-make fakeroot
$ dh_make

```

Usually what you are installed is a single binary, so press "s" then "enter".
Finally
```

$ fakeroot debian/rules binary

```
If there is an error at the configuration, it should tell you what package you need, lets say it tells you, that you need Glade. We go
```

$ sudo apt-cache search glade

```
We see that glade-2 comes out in the search list so we go
```

$ sudo apt-get install glade-2

```
I usually open Gedit and copy what files its installing incase they are the wrong ones, after its installed. Try the configuration again if everything goes well, then you should have a .deb package in the back directory. So to install that we do.
```

$ sudo dpkg -i ../package.deb

```

Whew.

Thats pretty much there is to it.  I think getting exposed to this can really bring you closer to understanding more of the linux, mainly debian based distros, world.  As you can see we usally try to make everything .deb so we can keep track of them with apt-get or Synaptic.

Well.  Good luck. :)

---

### Post by cwaldbieser on 2006-02-05
[QUOTE=*desk*]Hi All

Took me quite a while to find the New Thread icon.

I've used Windows for a fair amount of years, Windows 95 and even version 3.11.
Yesterday I decided to turn over a new leaf, and jump blindfold into Linux.

I found Ubuntu by chance, wiped XP and installed with no problems apart from not recognising my SoundBlaster and Lexmark printer.

The Distro is working very well but I just don't know how to run an application once I download it..... In Windows I just double click. There are DEB and RPM and even TGZ folders which I can unzip but get no further.  There must be a simple answer but I'm too Windows orientated to find it......otherwise I think I am going to enjoy this new experience but I think I will be knocking on your door a fair amount.

Des Kinsman[/QUOTE]
As far as installing software goes, try this link:
[http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")
You should basically install from the repositories when possible, as you then don't have to manually track dependencies yourself.  Installing a .tgz from source takes a little getting used to.

As far as running programs goes, some will create entries on the menu.  You can almost always open a terminal and type in the program name if it is in your command path.  The names tend to be case sensitive.  Try typing just the first few letters and then <TAB> to get the auto-complete feature to kick in.

---

### Post by *desk* on 2006-02-05
Thanks Guys

As you know this is new territory for me.

I have tried several of your suggestions but nothing as yet.

How do I save the terminal?

Sometimes it asks for a password but I can't type it in.....HELP!

Des Kinsman

---

### Post by Perfect Storm on 2006-02-05
It's for the security that you can't see what you're typing when enter the password.

---

### Post by Terry of Astoria on 2006-02-05
I don't know what you mean about "save the terminal" but you will find that at the terminal prompt, you can use the arrow keys on the keyboard (up arrow) to browse your recent commands.
Also your password will not appear even as dots or stars, but it is going in. You just type and hit enter.

---

### Post by lila on 2006-02-05
[QUOTE=*desk*]Thanks Guys

As you know this is new territory for me.

I have tried several of your suggestions but nothing as yet.

How do I save the terminal?

Sometimes it asks for a password but I can't type it in.....HELP!

Des Kinsman[/QUOTE]

You CAN type the password, it just doesn't show up.  DOn't know why, just type and hit ENTER, it'll work.
I'm not sure what you mean by save terminal.  If you mean saving it as a record of what you've done, I think it does that automatically, and there is a command to make it show all you've done, but I'm not that far yet...
I just copy and paste into an openoffice writer document if I want to keep track of something, I can then store all things related to a problem in one folder.
If you mean make it save your changes and commands, I think once you have hit ENTER in terminal, that's it, there is no "save changes y/n", it just does.  I also learned from somewhere (can't remember where) that the best (cleanest) way to leave terminal when you are finished is to type exit and then hit ENTER, rather than click on the X in the corner of the Window.
Lila

---

### Post by *desk* on 2006-02-05
Thank you once more....your responses are so speedy.

I believe I have an idea now  why I am doing wrong...I'll keep practicing.

Des Kinsman

---

### Post by *desk* on 2006-02-05
Hi Everyone

I have attempted to install only a DEB application and I get the message, "Could Not Open" and "Archive type not supported"
Must be doing something radically wrong.

Also I can't find the terminals I have written.

Des KinsmanI

---

### Post by Perfect Storm on 2006-02-06
If you find the terminal (when open it should be in the lower panel somewhere) please post the terminal output also what you typed in the terminal.

---

### Post by annsachd on 2006-02-06
Just curious, what programs are you downloading?

Have you tried downloading programs with Synaptic? It usually places a link to the program in the menus up above.

Hang in there friend, you're going to get the hang of this yet!

---

### Post by *desk* on 2006-02-06
This is the error message I get when I try and launch Audacity[ATTACH]5900[/ATTACH]

---

### Post by Perfect Storm on 2006-02-06
If you have enable universe there's a very easy way to install it.


```
sudo apt-get install audacity
```

about the .deb file you have:

```
cd /where/the/package/is
sudo dpkg -i XXXXXXX.deb

```

or
```
sudo dpkg -i /blah/blah/blah/blah/XXXXX.deb
```

---

### Post by *desk* on 2006-02-06
Thank You

I now have audacity installed.

First problem solved....many more to come, but enjoying every minute.

Des Kinsman

---

