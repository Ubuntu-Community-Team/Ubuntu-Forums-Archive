---
title: "application install question"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2006-04-02
This seems like it should be easy but I wish to install a downloaded program which was downloaded as a tarball that I have extracted but now what?  The site for the program says:

cd to castpodder then ./install.sh

(castpodder is the program, a podcast aggregator)
Problem is, I don't know what the instruction "cd to castpodder" means!  I tried the "./install.sh" in Terminal but only get error reply, "bash: ./install.sh: No such file or directory" so I figure there is a step I'm missing.
Help please & thanks as usual.

---

### Post by stoeptegel on 2006-04-02
cd .. means Change Directory.
When you're in /home/flyingsolo/ and you type *cd castpodder*```

flyingsolo@computername:~$ cd castpodder
```

You would you to the directory castpodder in your user directory. (off course only if there is a folder named castpodder)

---

### Post by flyingsolo on 2006-04-02
[QUOTE=stoeptegel]cd .. means Change Directory.
When you're in /home/flyingsolo/ and you type *cd castpodder*```

flyingsolo@computername:~$ cd castpodder
```

You would you to the directory castpodder in your user directory. (off course only if there is a folder named castpodder)[/QUOTE]

Thanks but there isn't a user directory called castpodder.  When I extract the tar file, it extracts it to the desktop with a file called castpodder which has multiple contained files.
This is the 1st program I've tried to load without Synaptic manager (I didn't find this in any repository; it was reviewed in Cooking with Linux in Linux Journal recently)

---

### Post by Qrk on 2006-04-02
Then you need to do this:

```
cd ~/Desktop/castpodder
./install.sh
```

cd works like

cd /path/to/directory

where ~ means /home/username in shorthand

---

### Post by flyingsolo on 2006-04-02
Thanks Qrk, this looks promising but now I get the message:

Checking UID...
Sorry, you have to be 'root'. Please su(do) and try again

If I type in sudo, I'm given multiple options to place after sudo but I don't recognize what they each do or which one I would need (see below)  Are these commands explained somewhere?  Which applies for me here? 

usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }

Thanks.

---

### Post by taurus on 2006-04-02
If you want to install something to the system, you need a write permission and only root can do that.  So, do
```

sudo ./install.sh

```

---

### Post by Sutekh on 2006-04-02
Use ```
sudo ./install.sh
```

---

### Post by flyingsolo on 2006-04-02
Thanks to Sutekh & Taurus, I now have the program running.  It says I still need the xmms player or Beep Media player.  I guess Rhythmbox doesn't cut it. 

I still want to know how to learn about the Terminal codes and where I can read about the meaning of all the codes.  I've learned a very small number of them by coping & pasting instructions provided in the forums but where can I read up on this and get some skill in using the Terminal?

---

### Post by taurus on 2006-04-02
If it needs xmms, then install it with apt-get then...
```

sudo apt-get install xmms

```

---

### Post by Sutekh on 2006-04-02
[QUOTE=flyingsolo]
I still want to know how to learn about the Terminal codes and where I can read about the meaning of all the codes.  I've learned a very small number of them by coping & pasting instructions provided in the forums but where can I read up on this and get some skill in using the Terminal?[/QUOTE]
You can try the link in my signature.

You can also try these links

[Ubuntu Wiki - Basic Commands]("https://wiki.ubuntu.com/BasicCommands")

[O'Reilly Net.com - Alphabetical Directory of Linux Commands]("http://www.oreillynet.com/linux/cmd/")

[ An A-Z Index of the Linux BASH command line]("http://www.ss64.com/bash/")

[The Linux Documentation Project -  Text-Terminal-HOWTO]("http://www.tldp.org/HOWTO/Text-Terminal-HOWTO.html")

[UNIX Guide.net - Linux Shortcuts and Commands]("http://www.unixguide.net/linux/linuxshortcuts.shtml")

---

### Post by flyingsolo on 2006-04-02
Thanks Taurus, I already got it via Synaptic.
Still, where to learn coding of instructions in Terminal except by directions I get from other forum members?

---

