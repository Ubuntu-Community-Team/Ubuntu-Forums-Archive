---
title: "cannot play flsh content in opera and FF"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by poisonblack on 2007-12-10
Hi all.!!

I can't seem to be able to play flash content on webpages in both opera and FF.Firefox is able to play some flash in swf format,while it fails for flv videos.opera 9.50b fails in both.How do I get them working.??

sudo apt-get install flasplugin-nonfree shows that it is already installed.

Also,How do I properly use the cd command.??I have a folder called flash on desktop,but I open terminal and type cd flash and it gives me an error no such file or directory.

Thanks.!!

---

### Post by KIAaze on 2007-12-11
cd = change directory

When you open a terminal, you are in your home directory by default, i.e. "/home/login".

If "flash" is on your Desktop, you can use one of these after opening a terminal:
```
cd Desktop/flash
cd /home/login/Desktop/flash
cd ~/Desktop/flash
cd ./Desktop/flash

```

"~" = /home/login
"." = current directory (=/home/login in this case)
".." = parent directory (=/home in this case)

To see where you are, you can use the command "pwd" (= print working directory).
But usually, it will be displayed in the command prompt.


For the flash issue, I don't know. I personally never had any problems with flashgames or youtube videos, so I don't really know.
I have "flashplugin-nonfree" installed and it works. :/
My first guess would be that the plugin is not well integrated with the browser.

How do you know when it's .swf or .flv? Can you give me an example of a site that doesn't work?

---

