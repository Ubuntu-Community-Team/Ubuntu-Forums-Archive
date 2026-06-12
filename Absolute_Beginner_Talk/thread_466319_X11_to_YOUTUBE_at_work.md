---
title: "X11 to YOUTUBE at work"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by tipalm73 on 2007-06-06
Hi,

I am at work and we have surf control. I would like to putty into my home machince and be able to view youtube or any other blocked sites.

Now at home I have it set up where i do ssh -X [email]user@mymachine.mine.nu[/email] FROM a linux machine to my server. Then type firefox [http://website.com](http://website.com), and the website shows up on the machine I am sshing FROM.

Now I am at work trying to use Putty. I have tried mymachine.mine.nu:0 and localhost:0 but each time i get this error:

 ```
The application 'firefox-bin' lost its connection to the display localhost:10.0;
most likely the X server was shut down or you killed/destroyed
the application.

```

Any help would be greatly appreciated.

Thanks in advance.

---

### Post by Rocket2DMn on 2007-06-06
I don't believe putty allows the creation of separate windows by command.  I think you need a more complete SSH client, though I'm not sure if there are any good free ones.
For example; when I connect to my school's UNIX system, I cannot open emacs in separate windows from putty, I can only work within the putty window.

---

### Post by microsoft92sucks on 2007-06-06
I don't know how to fix that but this site works ztunnel.com just put in the web site url you want to go to at that site and you can get on blocked sites. I used it at school.

---

### Post by jfinkels on 2007-06-06
You must have an X server running on the machine at work.

I don't really know about PuTTY, but if it doesn't support X forwarding for some odd reason, take a look at OpenSSH, I prefer it.

---

### Post by tipalm73 on 2007-06-06
> **Rocket2DMn said:**
> I don't believe putty allows the creation of separate windows by command.  I think you need a more complete SSH client, though I'm not sure if there are any good free ones.
For example; when I connect to my school's UNIX system, I cannot open emacs in separate windows from putty, I can only work within the putty window.

This makes me sad. 

I dont know why it works at home though? Granted it is Linux to Linux, but I am not using a local IP I am using the URL.  ssh -X [email]user@mymachine.mine.nu[/email]. I MUST WIN!

---

### Post by Cypher on 2007-06-06
You need X-Windows running on your Windows machine to be able to show Firefox. Cygwin not only has SSH but also X-Windows, so install that on your PC and then from the Cygwin BASH shell, you can use the same commands you use on your Linux machine and it'll all work..

---

### Post by tipalm73 on 2007-06-06
> **jfinkels said:**
> You must have an X server running on the machine at work.

I don't really know about PuTTY, but if it doesn't support X forwarding for some odd reason, take a look at OpenSSH, I prefer it.

It says it supports X Forwarding has little config area specific to that.

I appreciate the ztunnel.com link. Ill use that til I get this figured out =]

---

### Post by jdrodrig on 2007-06-06
I am new to this in general, but at school I have used Hummingbird Exceed but I do not think is for free. Some friends have used Cygwin/X that I think is opensource.

---

### Post by tipalm73 on 2007-06-06
Well I got cygwin/x installed on on my work xp machine.

I can ssh -X [email]user@mymachine.mine.nu[/email], but when I try to start firefox i get this error:
```
<firefox-bin:15543>: Gtk-WARNING **: cannot open display:
```

I installed all of X11 and open-ssh and telnet.

Need more info?

Thanks in advanced!

---

### Post by tipalm73 on 2007-06-06
Got it to work! YAY!

Wasnt starting correctly..still isnt i suppose. I get the following error msgs but it works and is very slow:

tim@tipalm:~$ firefox [http://youtube.com](http://youtube.com)

(firefox-bin:15641): Gdk-WARNING **: Connection to display localhost:10.0 appears to be untrusted. Pointer and keyboard grabs and inter-client communication may not work as expected.

(firefox-bin:15641): Gdk-WARNING **: Coercing GDK_INPUT_ONLY toplevel window to GDK_INPUT_OUTPUT to work around bug in Xorg server

(firefox-bin:15641): Gdk-WARNING **: Coercing GDK_INPUT_ONLY toplevel window to GDK_INPUT_OUTPUT to work around bug in Xorg server

(firefox-bin:15641): Gdk-WARNING **: Coercing GDK_INPUT_ONLY toplevel window to GDK_INPUT_OUTPUT to work around bug in Xorg server

How can I improve performance?

---

### Post by bukwirm on 2007-06-06
Firefox over an SSH connection is usually very slow - for me, at least.
You could try using a light-weight browser such as dillo.

---

### Post by Lord Illidan on 2007-06-06
Why not make a proxy that uses your home machine to connect to the internet?

---

### Post by bukwirm on 2007-06-06
By the way, trying to sidestep the restrictions established at your workplace is somewhat likely to get you into trouble, so you might want to be careful.

---

### Post by homergreg on 2007-06-06
Good job on getting cygwin working!  I really wonder if there is enough bandwidth in your connection at home to serve exported x11 video and audio back to you.  If you want to use your home computer to bypass blocked sites at work, I'll bet there is an HTTP proxy server application that you could use on your home computer, but that still may not be enough to serve video, or just use that ztunnel.com proxy server and youtube works great, at least until they block ztunnel.com!

(edit: looks like Lord Illian was thinking the same thing as I was posting this)

---

### Post by tipalm73 on 2007-06-07
Well I am ashamed to admit it but I am not sure how to do the proxy setup =[

ztunnel is blocked =[

Book I appreciate the suggestion. Honestly there isnt much that I look at that is surfcontrolled. I probably wont use it..I just like to know I can and always love a challenge =]

PS what would happen if i tried to save a file from the Xwindow?

---

### Post by punx45 on 2007-06-07
im a little fuzzy on the details, but i SSH tunnel from work through toaster to see mythb0x on my home LAN.   you might be able to accomplish something similar for youtube through your machine at home.   puTTY can tunnel.

ditto on the this could get you fired warning

---

### Post by tipalm73 on 2007-06-07
While I have your attention.

What are ssh clients written in? Know any place where I could look at the code in an ssh client?

Thanks for the input.

---

### Post by punx45 on 2007-06-13
my wild hunch says puTTy is written in C or something similar.   the source for puTTY is available [here]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html") .  others will vary.

---

