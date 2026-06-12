---
title: "[SOLVED] mIRC on Wine"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by mdsmedia on 2005-11-14
I've installed Wine...not a problem. Now I want to run mIRC on Wine.

I've got it on a USB drive that Linux will read.

I've done a bit of reading on the winehq website...but it seems to bypass the bit about how to actually get the exe file into a folder so Wine will read it and execute it.

I might be missing something, and maybe I'm just impatient. But it's one of the things that is keeping me from just staying on my Ubuntu partition and not booting to "some other OS"

---

### Post by frodon on 2005-11-14
Why not use xchat or another linux IRC client ? It would be easier
What makes you prefer mIRC than other IRC clients ?

---

### Post by mdsmedia on 2005-11-14
I knew this question would come up...but I didn't think it would come up so early :)

I've used x-chat, and I like it. I've used Konversation....sorry but I used x-chat first and I like it better :)

I've used mIRC for 9 years and I'm an op in a mIRC help channel. I like it and I'm familiar with it.

For just chatting and running a channel I'd be happy with x-chat. It does some things better than mIRC. But I've got things setup in mIRC that I like and it's hard to help people in a client I can't use.

As I get more used to x-chat I may move over. As I said I like it but I'm comfortable with mIRC and I've got other reasons to use it.

For now I'd like to be able to use mIRC and switch to x-chat without having to reboot.

---

### Post by frodon on 2005-11-14
lol, i understand.

I'm not sure you will need the latest version of wine, so open synaptic and install the wine and the winesetuptk packages. Then run winesetuptk in a terminal to configure wine.
Download the mIRC install file where you want and install it using a command like that : "wine setup.exe"
If you follow the basic installation mIRC will be installed in /home/username/.wine/fake_windows/Program files/mIRC or something like that.
Then all you have to do is to create an icon which run this command : "wine /home/username/.wine/fake_windows/Program files/mIRC/mIRC.exe"

I never tested that mIRC works with wine but i think it might work.

---

### Post by Pan007 on 2005-11-15
I have a question regarding IRC client.

I mostly do DCC with the IRC client and I can't get this to work with X-Chat.
Can anyone help me to set this up?

I have used mIRC and I really like it, and when it comes to DCC with this client, I have no problem. Can I install wine, mIRC and do DCC?

I really would like things to work under ubuntu and DCC is one thing I would like to work.

Don't like LimeWire, aMule...they're too slow.

---

### Post by Kvark on 2005-11-15
To use DCC in X-Chat, right click on a nickname and choose "Direct Client to Client" it is the secound item in the list.

mIRC works fine with wine. I kept using mIRC for a couple months after switching to Ubuntu without any problems. Eventually X-Chat got me though, it's a damn nice chat program.

---

### Post by Pan007 on 2005-11-15
Thanks for the quick reply....this forums never stops to amaze me.

What about XDCC in X-Chat....how is this done? Don't need to set up an server, but need to download.

---

### Post by Pan007 on 2005-11-15
I have installed wine with the excellent [COLOR="Red"]**[[COLOR="Red"]Automatix[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix")**[/COLOR].

I have one question...as I'm a newbie when it comes to wine.

How do I install/run mIRC? 

How do I install/run other win32 software?

Is there a GUI way to do this?

---

### Post by Kvark on 2005-11-15
Usually you install it by clicking on some file called setup.exe or autorun.exe and then run it by clicking on a program.exe file. You can make a shortcut point to it by entering "wine /path/to/program/program_file.exe" as the shortcut's command.

---

### Post by mdsmedia on 2005-11-18
Kvark,

That's a solution in Windows. How is it installed in Wine on Linux? Or have I missed something?

---

### Post by Kvark on 2005-11-18
Thats how you install Windows programs, period. They are packaged with .exe installers so thats what you gotta use to install them, even in Wine.

The only way around it if Wine would fail to run the installer is to install the program on Windows. Then copy paste the installed directory to Wine. In many cases you will also have to find and export the stuff it put in the Windows registry, then import that stuff to the Wine registry. You can open Wine's reg editor by typing regedit in a terminal.

---

### Post by mdsmedia on 2005-11-18
OK.....not questioning what you say...but then, where do I run the .exe file? "That's how it's done within Wine" How is it done? I'm new here!

---

### Post by Kvark on 2005-11-18
1. GUI way: It should work to click on the .exe file in nautilus or whatever file browser you are using.

2. CLI way: type "wine /path/to/the/file/file_name.exe".

---

### Post by mdsmedia on 2005-11-18
Thanks. That's clarified it.

---

### Post by xdefconx on 2008-01-08
I would like to know it is XChat possible to manage/connect/configure with terminal? My scenario is i would like to access my Ubuntu from different location through SSH/terminal. My point using IRC/Xchat/ coz i want to get a real time IP address from my dynamic IP connection. Everytime my Ubuntu reboot then my IRC/Xchat will automatically run and connect to IRC server, then me on different location just whois that domain so i can get that IP. That Ubuntu already up & running so i cant access it in front of that box unless remotely via SSH/terminal.

If Xchat cannot be done in terminal, may i know others IRC client that i can manage/connect/configure with terminal?

Thanxs

---

### Post by Standy on 2008-05-01
I've installed mIRC with wine, and chatting etc works great.. however, when i try to get into the script menu it get's all cranky and fuzzy and closes the whole application (mIRC) i am a major mIRC geek, and i love to script... anybody that is really familiar with mIRC on wine?

---

### Post by mdsmedia on 2008-06-15
> **Standy said:**
> I've installed mIRC with wine, and chatting etc works great.. however, when i try to get into the script menu it get's all cranky and fuzzy and closes the whole application (mIRC) i am a major mIRC geek, and i love to script... anybody that is really familiar with mIRC on wine?I've found that too, but haven't had a chance to really work on mIRC in Wine. It's one of my "to-do's"

I've found simple scripts can be manually added in the text box...ie. /alias etc....but trying to edit a script in mIRC's editor usually leads to it crashing.

---

