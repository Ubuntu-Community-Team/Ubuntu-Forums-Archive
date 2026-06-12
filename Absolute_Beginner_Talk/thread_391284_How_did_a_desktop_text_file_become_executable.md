---
title: "How did a desktop text file become executable?"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2007-03-23
I'm testing Feisty, and one of the latest updates boinked many people's wireless cards, including mine. So, at every bootup, I have to enter several commands in a terminal to get a working connection up and running. Rather than type them in every time, I saved them to a text file on my desktop, so i could just copy and paste each line.

I've been doing this - opening up the text file, copying and pasting lines to a terminal - for about a week now. This last time, I got a prompt saying that it was executable, and asking if I want to run it as such. As far as i could tell, it worked. Here i am online right now.

How did this happen? And is it that easy to make a little utility in Ubuntu?

---

### Post by devnulljp on 2007-03-23
You made a shell script
You can do it any time you like. Take a bunch of commands you normally type at the console, stick them in a file, top it off with #!/bin/sh and then do chmod +x <filename>. You can then run all those commands simply by running that file...

e.g., I have a tiny script to replace spaces with underscores in a working directory that usually has lots of windows-generated files in it with spaces that I back up to gmail (which doesn'tseem to like spaces). it got tiresome doing
rename 's/\ /_/g' *
on that directory all the time, so I packaged that command into a script and dumped it into my ~/bin directory (so it's in my $PATH). Now I just call the scriptname from the working directory  before uploading to gmail (of course I could just do it with cron).

#!/bin/sh
rename 's/\ /_/g' *

---

### Post by Foudre on 2007-03-23
really, you have to stick that at the top, I made one for mounting my external hard drive, but i just put in the mound command and what not, no #! /bin or what ever at the top, i just right clicked, permissions and clicked is executable, and it works

---

### Post by macogw on 2007-03-23
#!/bin/sh isn't always necessary.  I think the reason that line exists is so that if you're using a different shell, you can change it to reflect what shell and it'll do that.  If you use the default one, it'll work without it.

I think.

---

### Post by ricardisimo on 2007-03-23
It must not be necessary, because i certainly didn't add it. Does Feisty maybe have the capacity to anticipate file usage? "He's done this the past twelve times - he's probably going to do this again" or some such thing.

---

### Post by Foudre on 2007-03-23
file usage prediction is just sort of linux thing, I've noticed media formats don't need to have teh file extension, so it must be built in to scan the contents of a file

---

### Post by dptxp on 2007-03-23
I have a few text files with .asm extensions, yes they are assembly language source codes for some processor. When I click on them, I face the same dialog box in Ubuntu 6.10. Once every time the text editor GEDIT opens.

---

### Post by mcduck on 2007-03-23
> **Foudre said:**
> file usage prediction is just sort of linux thing, I've noticed media formats don't need to have teh file extension, so it must be built in to scan the contents of a file

Linux always checks what's inside the file to decide what kind of file it is. But adding the line to tell that it's a shell script and what shell it's made for is a good practice, so I'd recommend doing it at least if you are going to distribute the script to other people. It doesn't always make any difference, but sometimes not having it can cause the script to fail working (for example when somebody is using a different shell)

---

### Post by infol on 2007-03-23
an  easy 'script' for fixing broken fglrx/beryl after kernel upgrade...


 ```
#!/bin/sh

apt-get update
apt-get install linux-headers-`uname -r`
modprobe fglrx
depmod -a
```

make sure you are root when running the script... ;)

---

### Post by mcduck on 2007-03-23
> **infol said:**
> an  easy 'script' for fixing broken fglrx/beryl after kernel upgrade...


 ```
#!/bin/sh

apt-get update
apt-get install linux-headers-`uname -r`
modprobe fglrx
depmod -a
```

make sure you are root when running the script... ;)

If you have correct metapackage installed for your kernel you won't ever need that. :D If you are using generic kernel, make sure you have linux-generic, for 386 kernel linux-386 and so on.. New kernel header and restricted modules will be automatically installed for you with new kernels.

---

### Post by infol on 2007-03-23
> If you have correct metapackage installed for your kernel you won't ever need that. 

May be so, but only under feisty have I NOT had to manually install the restricted headers and load the fglrx-module. 

In neither dapper nor edgy, it would do this automagically... Maybe I was just unlucky, or maybe this little bash-script will help some (who've had the same issues as me)  :)

---

