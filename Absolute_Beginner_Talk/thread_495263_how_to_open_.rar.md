---
title: "how to open .rar ?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by retro_killa on 2007-07-07
i have alot of .rar files that i want to open i am useing Ubuntun/kbuntu so how can i open the .rar file & extract the .iso ?

[IMG]http://i65.photobucket.com/albums/h216/retro_killa/Screenshot.png[/IMG]

---

### Post by RomeReactor on 2007-07-07
Hi. Open Synaptic (or Adept in Kubuntu) and search for **unrar**; install it, and now the archiver/unarchiver applications (File-Roller in Ubuntu, Ark in Kubuntu) will be able to extract .RAR files.

---

### Post by atria on 2007-07-07
Install the unrar program
```
sudo aptitude install unrar
```

You should be able to open the archive with the archiver included in ubuntu afterwards. Good luck.

---

### Post by Qwerty_ on 2007-07-07
Alternatively you could type sudo apt-get install unrar in the terminal. Which does the same thing as going to synaptic.

---

### Post by Qwerty_ on 2007-07-07
Atria you beat me to it.

---

### Post by retro_killa on 2007-07-07
> **RomeReactor said:**
> Hi. Open Synaptic (or Adept in Kubuntu) and search for **unrar**; install it, and now the archiver/unarchiver applications (File-Roller in Ubuntu, Ark in Kubuntu) will be able to extract .RAR files.



tryed the search & nothing came up i am useing ubutun 6.0.6 with the packet upgrade of kubunt 

[IMG]http://i65.photobucket.com/albums/h216/retro_killa/Screenshot-1.png[/IMG]

---

### Post by Vague on 2007-07-07
Go to Settings>Repositories, enable Multiverse, close that, hit reload, search again.

---

### Post by vexorian on 2007-07-07
that's odd, just tried 7.04 and it is available, and I do remember that it was available in 5.04.

Try with the command line.

---

### Post by atria on 2007-07-07
Unrar is not included in the default ubuntu repository.

I think it is possible to enable the multiverse repositories through synaptic.

After including the multiverse repository, click reload and try searching again.

---

### Post by Qwerty_ on 2007-07-07
Best way to do it is to go System>Administration>Synaptic.

Now once you have opened up synaptic go to settings>repositioies. Then tick the boxes for mulitverse.

Once you have done that refresh your repos via synaptic or by typing sudo apt-get update in the terminal.

Then search for unrar in either synpatic or sudo apt-get install unrar.

Hope that helps.

---

### Post by KIAaze on 2007-07-07
In the worst case **(installing through Synaptic as suggested previously is indeed better)**, just download it from the WinRAR site:
[http://www.rarlab.com/rar/rarlinux-3.7.0.tar.gz]("http://www.rarlab.com/rar/rarlinux-3.7.0.tar.gz")

These commands should do everything, including downloading:
```
wget http://www.rarlab.com/rar/rarlinux-3.7.0.tar.gz
tar -xzvf rarlinux-3.7.0.tar.gz
cd rar
sudo make install

```

---

### Post by RomeReactor on 2007-07-07
As **Vague** said, enable "Multiverse" repositories and then install unrar; also remember that the file to extract is **np-mvuo64.rar** (so that it pulls with it all the rest, np-mvuo64.r01, np-mvuo64.r02, etc).

---

### Post by retro_killa on 2007-07-07
> **atria said:**
> Unrar is not included in the default ubuntu repository.

I think it is possible to enable the multiverse repositories through synaptic.

After including the multiverse repository, click reload and try searching again.



is it one of these ? 

[IMG]http://i65.photobucket.com/albums/h216/retro_killa/Screenshot-2.png[/IMG]

how do i install right click mark for install ... ? 

also how do i run the program once it is installed ?

---

### Post by retro_killa on 2007-07-07
also i tryed useing this

sudo apt-get install unrar & got this 

[IMG]http://i65.photobucket.com/albums/h216/retro_killa/Screenshot-3.png[/IMG]

---

### Post by Vague on 2007-07-07
> **retro_killa said:**
> is it one of these ?

I think you may have enabled Universe, but not Multiverse.

---

### Post by retro_killa on 2007-07-07
> **Vague said:**
> I think you may have enabled Universe, but not Multiverse.

is there away i can do that in the Terminal ?

---

### Post by retro_killa on 2007-07-07
[IMG]http://i65.photobucket.com/albums/h216/retro_killa/Screenshot-4.png[/IMG]

---

### Post by retro_killa on 2007-07-07
still un-able to unpack .rar :(

---

### Post by Qwerty_ on 2007-07-07
Did you update your repos.

Click the reload button in Synaptic.

---

### Post by vexorian on 2007-07-07
Try with KIAaze's , it worked for me the other year.

---

### Post by Vague on 2007-07-07
> **retro_killa said:**
> is there away i can do that in the Terminal ?

Yeah, you shouldn't really have to if you're using Synaptic, but you can ```
sudo nano /etc/apt/sources.list
``` replacing nano with your editor of choice and uncomment the multiverse entries.  It's pretty easy to do in Synaptic, though.  Just make sure you're checking the boxes for "Software restricted by copyright or legal issues (multiverse)" as well as the universe ones, and that you're reloading afterwards.

---

### Post by retro_killa on 2007-07-07
> **Qwerty_ said:**
> Did you update your repos.

Click the reload button in Synaptic.



how do i update the repos ?

---

### Post by Vague on 2007-07-07
> **retro_killa said:**
> how do i update the repos ?

As Qwerty said, click the "Reload" button in Synaptic.

---

### Post by Qwerty_ on 2007-07-07
By clicking the reload button in synaptic its in the top left hand corner.

---

### Post by retro_killa on 2007-07-07
> **KIAaze said:**
> In the worst case **(installing through Synaptic as suggested previously is indeed better)**, just download it from the WinRAR site:
[http://www.rarlab.com/rar/rarlinux-3.7.0.tar.gz]("http://www.rarlab.com/rar/rarlinux-3.7.0.tar.gz")

These commands should do everything, including downloading:
```
wget http://www.rarlab.com/rar/rarlinux-3.7.0.tar.gz
tar -xzvf rarlinux-3.7.0.tar.gz
cd rar
sudo make install

```



thx it worked all the way untill sudo make install 

[IMG]http://i65.photobucket.com/albums/h216/retro_killa/Screenshot-4.png[/IMG]

---

### Post by KIAaze on 2007-07-07
It's definitely in the multiverse repositories for Dapper Drake (6.06).
So if you manage to enable the multiverse repositories in Synaptic, you should have no problems installing it.

Otherwise, you can also download the .deb package from here (choose i386 unless you know you have amd64 or powerPC):
[http://packages.ubuntu.com/dapper/utils/unrar]("http://packages.ubuntu.com/dapper/utils/unrar")

After that, all you need to do is double-click it and it should launch the installation process.
If not (since Dapper Drake is rather old), just use the following command in the directory where you downloaded the .deb package:
```
dpkg --install unrar_3.5.4-0.1_i386.deb
```
(adapt if you used the amd64 or powerPC package of course)

Once unrar is installed, you'll have to extract by command line since there's still no GUI for WinRAR under GNU/Linux (something not to hard to do, I'll think about it...).
Here's how:
```
unrar x file.rar
```

If you just type ```
unrar
```, you'll get a list of the main commands usable. ;)

[B]edit:
Sorry, I was busy typing all the previous. ^^
> thx it worked all the way untill sudo make install 
What error messages do you get?[/B]

---

### Post by Qwerty_ on 2007-07-07
Hmm that is the more complex way as you are going to have to compile the unrar programme yourself.

---

### Post by retro_killa on 2007-07-07
dose this look right ? & how to i run the rar program now ? 

[IMG]http://i65.photobucket.com/albums/h216/retro_killa/Screenshot-6.png[/IMG]

---

### Post by Qwerty_ on 2007-07-07
Looks like you have installed it to me :)

---

### Post by KIAaze on 2007-07-07
Ok, perfect. It's installed. :)

Now, go to the directory where you downloaded your files, using the "cd" command and then use:
```
unrar x file.rar
```
----------------------
@Qwerty_:
> Hmm that is the more complex way as you are going to have to compile the unrar programme yourself.

No, because WinRAR only distributes the binaries (not open-source :( ).
When you run sudo make install, it basically just moves the binaries to the /usr/local/bin directory. ;)
In fact, the first time I installed it, I did that manually, I only discovered today that the Makefile could do it for me. ^^'

---

### Post by Qwerty_ on 2007-07-07
> **KIAaze said:**
> Ok, perfect. It's installed. :)

Now, go to the directory where you downloaded your files, using the "cd" command and then use:
```
unrar x file.rar
```
----------------------
@Qwerty_:


No, because WinRAR only distributes the binaries (not open-source :( ).
When you run sudo make install, it basically just moves the binaries to the /usr/bin directory. ;)
In fact, the first time I installed it, I did that manually, I only discovered today that the Makefile could do it for me. ^^'

Cool, last time when I tried it sometime last year I downloaded all the things required to compile. Silly me.

---

### Post by RomeReactor on 2007-07-07
**retro_killa**, if you already enabled the multiverse repository in Synaptic and clicked the blue **Reload**, unrar should appear in the search (you want **unrar**, not **unrar-free**). If it still doesn't show up (and you're sure you enabled the repository), enter this in the terminal:
```
sudo apt-get update
```
and
```
sudo apt-get install unrar
```
Just have patience; you'll see all of this shouldn't be as complicated as it's been so far ;)

EDIT: D'oh! Late again! :D
Oh, and the reason that **sudo make install** didn't work is because you probably don't have **build-essential** installed, I think.

---

### Post by retro_killa on 2007-07-07
wow thx everone it worked ;) i got the iso i needed ;) now lets hope the .iso dose install ;)

---

### Post by RomeReactor on 2007-07-07
Glad to hear you made it work!

I don't remember if this feature is in Dapper, but to burn it, right-click on it and select **Write to Disc...**

---

### Post by KIAaze on 2007-07-07
A bit off-topic:
> **Qwerty_ said:**
> Cool, last time when I tried it sometime last year I downloaded all the things required to compile. Silly me.

Hey, I didn't even know I could get the [source code]("http://www.rarlab.com/rar/unrarsrc-3.7.6.tar.gz"). :)
However, it only seems to allow extraction, not compression. (but the binary "rar" distributed does)
>  4. Legal stuff

   Unrar source may be used in any software to handle RAR archives
   without limitations free of charge, but cannot be used to re-create
   the RAR compression algorithm, which is proprietary. Distribution
   of modified Unrar source in separate form or as a part of other
   software is permitted, provided that it is clearly stated in
   the documentation and source comments that the code may not be used
   to develop a RAR (WinRAR) compatible archiver.

   More detailed license text is available in license.txt.


Well, I'm perfectly happy with tar, gzip and bzip for archiving. :p
And WinRAR can extract them on the Windows side. :)

---

### Post by Qwerty_ on 2007-07-07
Indeed plus Feisty has made everything so much easier. I just went sudo apt-get intall unrar and was done. Straight into the archive manager.

---

### Post by retro_killa on 2007-07-08
> **KIAaze said:**
> Ok, perfect. It's installed. :)

Now, go to the directory where you downloaded your files, using the "cd" command and then use:
```
unrar x file.rar
```
----------------------
@Qwerty_:


No, because WinRAR only distributes the binaries (not open-source :( ).
When you run sudo make install, it basically just moves the binaries to the /usr/local/bin directory. ;)
In fact, the first time I installed it, I did that manually, I only discovered today that the Makefile could do it for me. ^^'

100% working thx ;) :guitar:

---

### Post by wrongo on 2007-07-29
I double-click on the .rar file, and Archive Manager brings up a BLANK window, however with the title across the top bar thingie (the different-colored title bar that has the minimize, maximize, and close buttons at the extreme right - what's that called, the title bar??)

Anyway, I'm not ready to admit defeat, and I don't think it's my .rar file, because a right click on the file and a PROPERTIES selection reveals it's 700 Mb, which is a lot of data - SOMETHING should come up in the Archive Manager window...

Why is there NOTHING in the window?

---

### Post by KIAaze on 2007-07-30
What do you get when you run:
```
unrar lv <archive>
```
Available options (man unrar):
      e      Extract files to current directory.
       l      List archive content.
       p      Print file to stdout.
       t      Test archive files.
       v      Verbosely list archive.
       x      Extract files with full path.

Can you extract the contents?
```
unrar x <archive>
```
(or simply right-click, extract here with File-roller/Ark)

Does it work correctly with other .rar files?

---

