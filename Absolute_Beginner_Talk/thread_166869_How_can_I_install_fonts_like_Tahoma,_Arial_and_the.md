---
title: "How can I install fonts like Tahoma, Arial and the ones we use in windows?"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-04-27
I tried this command: ```
apt-get install win32 fonts
``` but it told me that no such package was found. I searched in synaptic but I couldn't find anything like that.

I hope somebody has a command for this. Especially for Arabic fonts.
Thanks

---

### Post by mjm115 on 2006-04-27
> 
apt-get install msttcorefonts


Please review [this]("https://wiki.ubuntu.com/FontInstallHowto") site.

---

### Post by penywise on 2006-04-27
Sorry for interrupting...

When we get those (or any) fonts installed -> can we change the font of the system (Gnome)... especially the Firefox font... ah it's...](*,) 

And how about switching between languages?
(actually what is the difference between getting a cyrilic (ect) font, and using it as a language, switching between it and the original one)

---

### Post by Jagot on 2006-04-27
This may help you as well:

[http://help.ubuntu.com/starterguide/C/ch03s03.html](http://help.ubuntu.com/starterguide/C/ch03s03.html)

---

### Post by Isoss on 2006-04-27
[QUOTE=mjm115]Please review [this]("https://wiki.ubuntu.com/FontInstallHowto") site.[/QUOTE]

Hey, thanks but it outputted this:
```
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

```

---

### Post by Jagot on 2006-04-27
You need to add the multiverse [corrected] repository if you have not done so already as that is where the msttcorefonts package lives:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by Isoss on 2006-04-27
Oh, I thought they already set to universe multiverse ... Thanks, it worked.

---

### Post by Isoss on 2006-04-27
Oh, sorry, I didn't notice the error in Terminal! after I typed the install command it asked me whether I want to continue or not so I thought everything went OK, then I noticed this error:
```
isos@ubuntu:~$ sudo apt-get install msttcorefonts
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  cabextract
The following NEW packages will be installed:
  cabextract msttcorefonts
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 66.8kB of archives.
After unpacking 315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://sy.archive.ubuntu.com breezy/universe cabextract 1.1-1 [44.7kB]
Get:2 http://sy.archive.ubuntu.com breezy/multiverse msttcorefonts 1.2ubuntu2 [2 2.1kB]
Fetched 66.8kB in 4s (16.7kB/s)

Preconfiguring packages ...
Selecting previously deselected package cabextract.
(Reading database ... 70959 files and directories currently installed.)
Unpacking cabextract (from .../cabextract_1.1-1_i386.deb) ...
Selecting previously deselected package msttcorefonts.
Unpacking msttcorefonts (from .../msttcorefonts_1.2ubuntu2_all.deb) ...
Setting up cabextract (1.1-1) ...
Setting up msttcorefonts (1.2ubuntu2) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--17:26:19--  http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.ex e
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... failed: Connection  refused.
--17:26:20--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32. exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... failed: Connectio n refused.
--17:26:21--  http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32 .exe
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... 207.250.4.12
Connecting to twtelecom.dl.sourceforge.net|207.250.4.12|:80... failed: Connectio n refused.
--17:26:21--  http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.ex e
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... 204.157.3.229
Connecting to aleron.dl.sourceforge.net|204.157.3.229|:80... failed: Connection refused.
--17:26:22--  http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.ex e
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... 195.113.161.88
Connecting to cesnet.dl.sourceforge.net|195.113.161.88|:80... failed: Connection  refused.
--17:26:23--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.ex e
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... 130.59.138.20, 2001:620:0:1b::20
Connecting to switch.dl.sourceforge.net|130.59.138.20|:80... failed: Connection refused.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::20|:80... failed: Network  is unreachable.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

WHAT'S WRONG?

---

### Post by Isoss on 2006-04-27
Somebody Help!

---

### Post by gingermark on 2006-04-27
[QUOTE=Isoss]Somebody Help![/QUOTE]
I take it you forgot to say "please"...

If you happen to have the ttf files (from a windows installation say) you can use those. I know how to do it in KDE, there is an option simply to load fonts.

I would assume Gnome has a similar option.

---

### Post by Jagot on 2006-04-27
Sometimes the sources from which these are obtained can be down - it looks like there were connection errors there.  You may want to try again later.

---

### Post by Isoss on 2006-04-27
[QUOTE=gingermark]I take it you forgot to say "please"...
[/QUOTE]
OK .. Sorry ... let me say it again: :p 

PLEASE ... SOMEBODY HELP! :( 
Cool now buddy?
Anyway ...
[QUOTE=gingermark]
If you happen to have the ttf files (from a windows installation say) you can use those. I know how to do it in KDE, there is an option simply to load fonts.

I would assume Gnome has a similar option.[/QUOTE]

I hope you'd explain this ttf files (cuz I am a rookie here) ...
The previous output didn't just show while trying to install msttcorefonts ... also something similar outputted while installing firestarter and aMSN and some other program ... so what's wrong with my repisitories? I simply edited all of them as as explained in this [PAGE]("https://wiki.ubuntu.com/AddingRepositoriesHowto") and for each of the Community Maintained (Universe) I changed from 'universe' to 'universe multiverse' .. 

So I need to know what did I go wrong?!

---

### Post by gingermark on 2006-04-27
I can't comment on the current method you're following - hopefully someone else can help you there.
I know very little about your situation, but if you are dual booting, then there is this directory in Windows called "Fonts". I think it's in the system directory - I haven't used windows for a while, so can't remember.

But you could look / search for it.

Anyways, in this directory are all the fonts installed on a windows system, and they are usually in format that I think is ".ttf"

So, if you wanted Arial, you'd copy across "arial.ttf" (for example) to your Ubuntu system, and then you should be able to add it to the fonts that are available for your system.

Unfortunately, as I said, I don't know how this would be done in Gnome. In KDE, there is a "font installer" setting - I would assume GNOME has something similar.

Of course, if you don't have a Windows install handy, this is all useless.


As far as the method you are currently following, you are having trouble downloading the fonts. Either the server is down (like Jagot suggested) or the files aren't there anymore. Hopefully it's not the latter.

---

### Post by Isoss on 2006-04-27
[QUOTE=gingermark]I can't comment on the current method you're following - hopefully someone else can help you there.
I know very little about your situation, but if you are dual booting, then there is this directory in Windows called "Fonts". I think it's in the system directory - I haven't used windows for a while, so can't remember.

But you could look / search for it.

Anyways, in this directory are all the fonts installed on a windows system, and they are usually in format that I think is ".ttf"

So, if you wanted Arial, you'd copy across "arial.ttf" (for example) to your Ubuntu system, and then you should be able to add it to the fonts that are available for your system.

Unfortunately, as I said, I don't know how this would be done in Gnome. In KDE, there is a "font installer" setting - I would assume GNOME has something similar.

Of course, if you don't have a Windows install handy, this is all useless.


As far as the method you are currently following, you are having trouble downloading the fonts. Either the server is down (like Jagot suggested) or the files aren't there anymore. Hopefully it's not the latter.[/QUOTE]

Alright buddy .. thanks ...I'll try your way. Thanks :)

---

### Post by Jagot on 2006-04-27
Following on from what gingermark has said, fonts with Windows are in your C:\WINDOWS\Fonts directory.

I do not believe there is a similar installer in GNOME so it has to be done the manual way, but it's not difficult.

The method I use only installs the fonts in Ubuntu for the user - they are not system wide.  To do this, in your home directory create a folder called .fonts

Now copy the fonts you want over and put them in this directory - I used a USB drive to get them from Windows to Ubuntu.

Finally you will need to run the following command from terminal:

sudo fc-cache -f -v

This makes Ubuntu recognise the fonts so it is able to use them.

---

### Post by Caligula on 2006-04-27
Actually...
I don't have it in universe...
And it's not logical that it'll be in universe, as you're not allowed to change it, redistribute it, or anything... It'll be in multiverse.

---

### Post by Jagot on 2006-04-27
[QUOTE=Caligula]Actually...
I don't have it in universe...
And it's not logical that it'll be in universe, as you're not allowed to change it, redistribute it, or anything... It'll be in multiverse.[/QUOTE]

Yep, you're correct, I was reading for xfonts.  He's managed to get the correct repository anyway thankfully though.

---

### Post by Isoss on 2006-04-27
Alright, thanks guys

---

### Post by brentoboy on 2006-04-27
the fonts are free, and they are all over the internet. google it msttcorefonts, you'll find lots of zip or tar.gz type downloads for them, I think gnome-looks.org has em.

anyway, download them and dump them here:
/usr/share/X11/fonts/truetype
create the folder if it doenst exist.

correct me if im wrong, but I think once they are in there, things just work--maybe you need to restart x, but I doubt it.

---

