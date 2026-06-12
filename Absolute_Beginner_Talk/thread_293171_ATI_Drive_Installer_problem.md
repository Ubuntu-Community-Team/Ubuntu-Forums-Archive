---
title: "ATI Drive Installer problem"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by flotsaminthecosmicsea on 2006-11-04
I am trying to install the latest driver for my ATI x800 graphics card.

I've downloaded the installer from AMD's website and was actually able to run it! But, when installation is complete, I get stumped at the last step, being the noob I am. The last step is:

[IMG]https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/images/inst8.30.3/linux_83.gif[/IMG]

mine says that the log file has been saved to /usr/share/ati

The instructions ATI gives at their site ([https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.30.3-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.30.3-inst.html))
says to 

"#  Launch the Terminal Application/Window and run  /usr/X11R6/bin/aticonfig --initial to configure the driver.  "

can someone give me the specific code for doing this? Furthermore, though I can locate the file in nautilus, I can't save it, and don't know how to run the autoconfig. I'm a noob, can someone shed light on this?

I've been able to find the

---

### Post by JoeMcC00L on 2006-11-04
To launch the terminal Application/Window hit alt+f2 and type gnome-terminal. This should bring up a console that looks something like :
user@computer:~$
this is where you should type in /usr/X11R6/bin/aticonfig --initial

I hope this answers your question!

---

### Post by flotsaminthecosmicsea on 2006-11-04
I know how to open the terminal window. I'm not that much of a noob. I would't even be able to use the internet if I hadn't put in about a dozen terminal commands. When I copy and paste the code ATI gives me, I get an unknown command error. I need to know that ATI is really trying to tell me to put in the terminal.

---

### Post by dbott67 on 2006-11-04
The command they want you to run is 'aticonfig --initial'.  Doing a search for the 'aticonfig' command, my computer returns:
```
dbott@dapper:~$ **slocate aticonfig**
[COLOR="Red"]/usr/bin/aticonfig[/COLOR]
/usr/share/doc/fglrx/examples/etc/acpi/events/a-ac-aticonfig
/usr/share/doc/fglrx/examples/etc/acpi/events/a-lid-aticonfig

```

So, on my computer, the little devil is hiding in **/usr/bin**, which is quite convenient as that directory is part of the path (meaning that the command will run from any directory).  Just type in **aticonfig --initial** in your home directory & the program should run.  If not, just cd to **/usr/bin**.

-Dave

---

### Post by flotsaminthecosmicsea on 2006-11-07
> **dbott67 said:**
> Just type in **aticonfig --initial** in your home directory & the program should run.  If not, just cd to **/usr/bin**.

-Dave

How do I do that. I know how to open up the terminal and enter commands. I'm not sure where they are running from. What do you mean by cd?

---

### Post by dbott67 on 2006-11-07
'cd' is the command to 'change directory'.  So, if you were in your home directory (also known as **~** or **/home/your_login_name**), you could issue the following command to change directories to **/usr/bin**:
```
cd /usr/bin
```

If the command is in the 'path', you can type the command in any directory and the computer will search through the path to see if it can find it.  If the command is not in the path, you have to change to the directory that contains the command and type:
```
./name_of_file
```

The preceding './' tells the computer to look in the current directory.

-Dave

---

### Post by flotsaminthecosmicsea on 2006-11-09
> **flotsaminthecosmicsea said:**
> How do I do that. I know how to open up the terminal and enter commands. I'm not sure where they are running from. What do you mean by cd?

Thanks, worked like a charm. My boxes drag nicely, but video and screensavers still suck at full screen? anybody know whats going on?

---

### Post by dbott67 on 2006-11-09
Can you post the output of:
```
fglrxinfo
```
and
```
fgl_glxgears
```
and
```
glxgears -printfps
```

-Dave

---

