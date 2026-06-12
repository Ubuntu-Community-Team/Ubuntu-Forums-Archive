---
title: "Ubuntu Documentation"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by vivin_west on 2006-12-18
There is so much documentation on Ubuntu that I am confused where to start. Is there a simple instruction manual which helps me config my system. I donot want to use the terminal window.

---

### Post by towsonu2003 on 2006-12-18
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html) (official ubuntu documentation, also available trhu System > Help > System Documentation) is usually a nice place to start. But if you tell what exactly you want to do, someone might be able to provide a better link.

---

### Post by benuski on 2006-12-18
[This]("http://psychocats.net/ubuntu/index") is always a good place to go too.

---

### Post by vivin_west on 2006-12-18
I wanted to install Java run time environment. I spent two hours figuring out how to two it. After that I discovered how it. It was just 4 clicks away and took 5 mins. 

I wanted to install a printer. I spent 2 days figuring out how to. I spent 4 hrs on the web. When I finally found out how to, It took me just 10 mins and 10 clicks. See where I am getting? I want to know how to use the mouse and not the terminal window and get things done.

---

### Post by benuski on 2006-12-18
Well, the community on these forums are really great, and usually you can get a response within minutes, and not hours or days like other fora.  So do you have any specific questions right now?

---

### Post by aysiu on 2006-12-18
If you don't want to use the terminal, I wouldn't recommend Ubuntu. There are only a few tasks that **require** the terminal, but almost all the instructions you get will be terminal commands. Honestly, though, you just need to copy and paste--you don't even have to retype them.

If you're still too afraid of the terminal, I would recommend Mepis, PCLinuxOS, or Freespire instead of Ubuntu.

That said, there are some very screenshot-heavy Ubuntu guides out there. benuski has linked to mine. There is also another popular one about installing software:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by vivin_west on 2006-12-18
FIne then, I just dint want to bother you and get things done myself but since you are telling me Forum and terminal is the best to solve the problem help me fix this problem.
I am not an expert with linux commands

vivinzdauser@vivin-desktop:~$ totem

(totem:7236): Gdk-WARNING **: locale not supported by Xlib

(totem:7236): Gdk-WARNING **: cannot set locale modifiers
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 69 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
vivinzdauser@vivin-desktop:~$

I am not able to run totem

---

### Post by aysiu on 2006-12-18
You're absolutely right on here. There's no way in hell anyone would be able to tell you what was wrong with Totem if you just posted a screenshot of it. Terminal is the way to go here.

Apparently, that bug has something to do with playing high resolution videos in Totem. It's been reported and presumably fixed?
[https://launchpad.net/products/totem/+bug/35229](https://launchpad.net/products/totem/+bug/35229)
[Video players (Totem, VLC, etc.) fail with BadAlloc error](http://ubuntuforums.org/showthread.php?t=194746)

P.S. The whole point of the forums is to "bother" people. We are all users here, and we're trying to help each other out. I've already linked to all the good point-and-click guides I know.

---

### Post by vivin_west on 2006-12-18
I still see no reason why you are so upset? I am using terminal window.It is not a screen shot. I just wanted to get totem running and I wanted to fix this problem.That is why I asked for instruction manuals. There is no point arguing any further. I will go through the guides and get it done myself.Thanks for your aid.

---

### Post by aysiu on 2006-12-18
I'm not upset. Sorry I came off that way.

---

### Post by steve.horsley on 2006-12-18
Aysiu:
There is a typo in your monkeyblog link above - it's missing a "y".

vivin_west: 
Don't get upset. Aysiu is really helpful and never seems to get offended - it's just that it's not always easy to tell someone's mood by reading their words.

I don't know what's wrong with your totem - that doesn't happen to me (I'm on Edgy). Can I suggest you try installing and gxine instead? I find that it plays more codecs than totem anyway.

You will find that most help offered in these forums is giving command-line instructions rather than GUI instructions because it is quicker and easier and more accurate both to give and to follow command-line instructions (use copy and paste - don't re-type by hand).

---

### Post by aysiu on 2006-12-18
Thanks. I've fixed the typo now.

---

