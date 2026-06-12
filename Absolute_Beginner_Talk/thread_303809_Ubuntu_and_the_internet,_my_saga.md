---
title: "Ubuntu and the internet, my saga"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by nonpareilpearl on 2006-11-20
This is my first post from my laptop!!! (as opposed to all the ones from my desktop while logged into Windows ;) )

As it ended up happening I came home and plugged in the laptop and the internet came back. I do not know why. I have discovered that now that I have the internet I need to enter the sudo dhclient (as suggested) before every attempt to get on the internet after booting the computer, although I do not know why.

My internet connection is still splotchy at best. My university apparently has a "ResNet" patch that we need to enter into some file (that I found) as "superuser" (that I also found :D ) in order to make it not take 5 minutes to load every page. Well I entered it, as directed, and after losing the internet completely on the first few boots it seems to work alright now (if no faster-I feel like I'm on dial up lol). The link to the fix is [here]("http://ubit.buffalo.edu/linux/ResNetLinuxFix.php"), and while this is not my current problem if anyone has any thoughts I would be most grateful :)

My current problem is that I tried to view a page that required the Flash plugin. I (stupidly, apparently) clicked on the "download plugin" in order to install it. Firefox went through the motions and installed it and now everytime I encounter a page with Flash on it Firefox terminates. I was going to try and remove it, but so far all I've found is to go into where the plugins are located via the terminal... I have no idea where that is (the plugins, I know where the Terminal is and I think we are becoming fast friends.. lol)

I think when I have all this figured out I shall write a FAQ page about this... called "Ubuntu and you-How to access the Internet 101".

---

### Post by dmizer on 2006-11-20
actually ... firefox is probably crashing because of problems with flash and sound.  you can find out what's causing a program to crash by running it from the command line.  when it crashes, it will display an error message in the cli which you can use to troubleshoot.

can't do that in windows ;)

if you don't know how, all you have to do to run a program in terminal is open a terminal and type the program name (in this case: firefox).

---

### Post by nonpareilpearl on 2006-11-20
I did as you suggested, and I recieved the following errors:> quintessence@Qubuntu:~$ firefox
** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 118 error_code 8 request_code 143 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Should I just remove the plugin (if so are there some instructions I can use)? Is there an alternative?

---

### Post by IYY on 2006-11-20
I am not sure what the exact problem is, but Flash 9 fixes many of the old problems with flash. Get it right here:

[http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

You just need to copy a single file from the archive into the appropriate directory as specified in the README.

---

### Post by nonpareilpearl on 2006-11-20
Everything keeps crashing. How would I remove the current firefox plugin? That's the problem... then I can install the next one :)

---

### Post by nonpareilpearl on 2006-11-20
Alright so I found the directory and I am going to remove the two files in there.... and hope I don't break anything.

---

### Post by drphilngood on 2006-11-20
Anything can be fixed if you break it.

---

### Post by dmizer on 2006-11-21
removal directions here: [http://www.adobe.com/cfusion/knowledgebase/index.cfm?id=tn_15380](http://www.adobe.com/cfusion/knowledgebase/index.cfm?id=tn_15380)

---

### Post by nonpareilpearl on 2006-11-21
Actually that was exactly what I tried doing, I was just worried about removing a library file :-s But now the new plugin works just  fine :)

I have noticed that most tutorials I have found will say things like "go to plugin folder" without saying where those are. After working on Windows machines for so long that while I can handle that sort of thing with any Windows OS, being new to Linux it was driving me batty. I had no idea where to look :-?

---

### Post by dmizer on 2006-11-21
> **nonpareilpearl said:**
> I have noticed that most tutorials I have found will say things like "go to plugin folder" without saying where those are.
unfortunately, since directory structure and naming conventions are different even within ubuntu, it's difficult to tell you "your plugin directory is here:"  to further complicate the issue, there are those who have jumped on the firefox 2.0 bandwagon and installed it in a different place.

so the problem here is the the "plugins" folder can be in any number of different places depending on your situation.

often, if you're not sure where to find something, you can go to terminal and try: whereis filename ... also slocate filename works for some things.

---

