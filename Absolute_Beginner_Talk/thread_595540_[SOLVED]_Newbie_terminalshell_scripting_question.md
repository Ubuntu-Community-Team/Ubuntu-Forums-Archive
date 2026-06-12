---
title: "[SOLVED] Newbie terminal/shell scripting question"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by kyalee on 2007-10-28
I'm trying to learn the terminal and basic shell scripting. The website I'm learning from is [http://linuxcommand.org/](http://linuxcommand.org/)

I just wrote newbie's first shell script which is just the basic Hello World script from the site.

```
#!/bin/bash
# My first script

echo "Hello World!"
```

Works fine. Where I'm running into trouble is with figuring out how to store my scripts in my path. According to the site: "Most modern Linux distributions encourage a practice in which each user has a specific directory for the programs he/she personally uses. This directory is called bin and is a subdirectory of your home directory." So I created a file called bin in my home folder.

When I type simply

```
my_script
```

I get 

```
bash: my_script: command not found
```

But when I type

```
bin/my_script
```

I get the desired

```
Hello World!
```

I figure the point is to not have to specify the pathname. So what am I doing wrong? It's probably something really, really simple that I'm missing. Hopefully one of you wonderful folks will take pity on a newbie and help me out. :)

---

### Post by kast on 2007-10-28
i would create you own bin or say **mybin** in a folder in your **$PATH** instead of adding you **/home/bin** to it. For security reasons you don't have your **$PATH** include your $HOME because if someone wanted to place say a BIN file that was a back-door say the "ls" command its going to search your path and get that hacked version when you issue a ls. create a /usr/local/mybin or something like that.

also make sure you make the script exacutable

**chmod +x myscript**

Sorry if i confused you! typing fast need to get back top the tube! :)

---

### Post by HermanAB on 2007-10-28
User scripts typically go into /usr/local/bin.

Cheers,

Herman

---

### Post by greenlegacy on 2007-10-28
Try typing this:
```

echo $PATH

```

I've not really done much shell scripting before, but I know that to run commands in the terminal the way you are wanting to do they must be added to your path.

I wouldn't really recommend adding your script to one of those directories though since they probably all require root access.  Try putting it in a different directory then add that directory to the path with this command:

```

export PATH=$PATH:YOUR_DIRECTORY

```

---

### Post by kyalee on 2007-10-28
Thanks all for the replies. I guess I read the website wrong. I thought I was supposed to create a file called bin in my home/[myusername] file. What I really should do is create a file for the scripts in my usr/local file? Is that right. Or do they go in the already created usr/local/bin file?

Sorry, I'm still learning my way around the linux file system. In windows I didn't pay attention to this stuff as long as I could find what I wanted, bu with linux I actually want to know how it works. *g*

---

### Post by kast on 2007-10-28
You can put them in your /usr/local/bin that will work, making your own bin  just makes it easier to keep track of your home grown scripts. 

you will notice going forward with Linux that most everything you install locally, will drop a file in your /usr/local/bin and it can get messy trying to keep track of your own scripts

---

### Post by greenlegacy on 2007-10-28
As far as the linux file system goes, I found [this image]("http://bp3.blogger.com/_Vbsj-yhipTw/RvaiatPBPBI/AAAAAAAAABs/yjx3hPlEUNw/s1600-h/linux_file_structure.jpg") that I feel really explains it well:

---

### Post by kyalee on 2007-10-28
Okay, that makes sense, thanks. :)

Two more questions, if you don't mind.

1. When I go to my usr/local file and right click to create a new folder, the create new folder area is grayed out so I can't click it. I know I could also type mkdir usr/local/mybin into the terminal but (a) I'm used to doing things like that via the GUI and I'm still getting out of the habit and (b) I want to make sure there's not something I'm doing wrong before I go trying it in the terminal.

2. When I peeked in my user/local/bin file, it was totally empty, even when I hit CTRL+H to show the hidden files. I've only been running Ubuntu for a little while (about two months), but I have tweaked the system somewhat. If things that I install locally are dropping files into the user/local/bin, shouldn't there be stuff in there? Or is it possible I just haven't tweaked anything that would drop a file in there?

greenlegacy - Thank you so much for the image. I've saved it to my tutorials folder and might even make it my wallpaper for a while. :lolflag:

---

### Post by Gremlinzzz on 2007-10-28
Theres absolutely nothing that cant be done with the right commands type or paste this command in terminal then check your home folder.
sudo ar m god

---

### Post by kast on 2007-10-28
to create a folder in /usr/local

**sudo mkdir /usr/local/mybin**

I only have like 8 things in my /usr/local/bin so if you haven't installed allot of stuff you might not have allot in there.

---

### Post by kyalee on 2007-10-28
I knew it before, of course, but this forum totally rocks. Thank you so much for all your help!

---

