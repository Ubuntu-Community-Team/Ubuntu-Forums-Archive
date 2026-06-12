---
title: "going top a webpage that ends in .swf"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by x-ray vision on 2007-04-12
A friend just sent me this link in an email:

[http://stwww.weizmann.ac.il/G-CS/BENARI/files/frogs.swf](http://stwww.weizmann.ac.il/G-CS/BENARI/files/frogs.swf)

When I click on it, I get "This page cannot be found".

I tried going to Synaptic and installing "swf-player" and that didn't help. Any ideas?

---

### Post by Stickymaddness on 2007-04-12
Which browser & desktop are you using? It loads fine for me in firefox under gnome....

---

### Post by Malakia on 2007-04-12
I just tried it and it says it can't find the page. Interesting....

---

### Post by bashologist on 2007-04-12
If you really want to see if the file there exists the best way would be wget.
```
neko@debian:~$ wget http://stwww.weizmann.ac.il/G-CS/BENARI/files/frogs.swf
--12:42:28--  http://stwww.weizmann.ac.il/G-CS/BENARI/files/frogs.swf
           => `frogs.swf'
Resolving stwww.weizmann.ac.il... 132.77.150.101
Connecting to stwww.weizmann.ac.il|132.77.150.101|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
12:42:28 ERROR 404: Not Found.

neko@debian:~$
```

---

### Post by x-ray vision on 2007-04-12
> **Stickymaddness said:**
> Which browser & desktop are you using? It loads fine for me in firefox under gnome....
Same as you, Firefox and gnome.

---

### Post by x-ray vision on 2007-04-12
Anyone know what it takes to make sites like this work?

---

### Post by x-ray vision on 2007-04-12
bump

---

### Post by bashologist on 2007-04-12
> **x-ray vision said:**
> Anyone know what it takes to make sites like this work?

It's not gonna work. The file isn't on the server. This is a swf: [http://wwwimages.adobe.com/www.adobe.com/swf/homepage/fma_shell/FMA.swf](http://wwwimages.adobe.com/www.adobe.com/swf/homepage/fma_shell/FMA.swf)

For more information read this: [http://en.wikipedia.org/wiki/404_error](http://en.wikipedia.org/wiki/404_error)

---

### Post by x-ray vision on 2007-04-12
> **bashologist said:**
> It's not gonna work. The file isn't on the server. This is a swf: [http://wwwimages.adobe.com/www.adobe.com/swf/homepage/fma_shell/FMA.swf](http://wwwimages.adobe.com/www.adobe.com/swf/homepage/fma_shell/FMA.swf)

All I see is a white rectangle on a black page.

---

### Post by x-ray vision on 2007-04-12
> **bashologist said:**
> It's not gonna work. The file isn't on the server. This is a swf: [http://wwwimages.adobe.com/www.adobe.com/swf/homepage/fma_shell/FMA.swf](http://wwwimages.adobe.com/www.adobe.com/swf/homepage/fma_shell/FMA.swf)

For more information read this: [http://en.wikipedia.org/wiki/404_error](http://en.wikipedia.org/wiki/404_error)

Okay, I just checked using Windows and my link doesn't work, but the one that you gave does and doesn't work for me in Ubuntu. Any idea why?

---

### Post by bashologist on 2007-04-12
> **x-ray vision said:**
> All I see is a white rectangle on a black page.

Paste the following into your terminal:
```
filename="install_flash_player_9_linux.tar.gz"; cd /tmp; if wget "http://fpdownload.macromedia.com/get/flashplayer/current/$filename"; then tar -xvvzf "$filename"; cd "${filename%%.*}"; sudo chmod a+x flashplayer-installer; sudo .flashplayer-installer; fi

```
This is my own tutorial for installing flash. It should work. When it's done then open your browser again and try this url to test it: [http://wwwimages.adobe.com/www.adobe.com/swf/homepage/fma_shell/FMA.swf](http://wwwimages.adobe.com/www.adobe.com/swf/homepage/fma_shell/FMA.swf)

---

### Post by ubuntu27 on 2007-04-12
The problem isn't that he dosn't have Flashh installed.
The "problem" is that THAT FILE REALLY DOES NOT EXIST.

I've tried to access it using Firefox and Opera in Windows. And sure enough, it can't find it.


The page cannot be found
The page you are looking for might have been removed, had its name changed, or is temporarily unavailable.

Please try the following:

    * Make sure that the Web site address displayed in the address bar of your browser is spelled and formatted correctly.
    * If you reached this page by clicking a link, contact the Web site administrator to alert them that the link is incorrectly formatted.
    * Click the Back button to try another link.

HTTP Error 404 - File or directory not found.
Internet Information Services (IIS)

Technical Information (for support personnel)

    * Go to Microsoft Product Support Services and perform a title search for the words HTTP and 404.
    * Open IIS Help, which is accessible in IIS Manager (inetmgr), and search for topics titled Web Site Setup, Common Administrative Tasks, and About Custom Error Messages.

---

### Post by x-ray vision on 2007-04-12
> **bashologist said:**
> Paste the following into your terminal:
```
filename="install_flash_player_9_linux.tar.gz"; cd /tmp; if wget "http://fpdownload.macromedia.com/get/flashplayer/current/$filename"; then tar -xvvzf "$filename"; cd "${filename%%.*}"; sudo chmod a+x flashplayer-installer; sudo .flashplayer-installer; fi

```
This is my own tutorial for installing flash. It should work. When it's done then open your browser again and try this url to test it: [http://wwwimages.adobe.com/www.adobe.com/swf/homepage/fma_shell/FMA.swf](http://wwwimages.adobe.com/www.adobe.com/swf/homepage/fma_shell/FMA.swf)

After it seemed to install something, I got "flashplayer-installer: command not found"

---

### Post by bashologist on 2007-04-12
> **x-ray vision said:**
> After it seemed to install something, I got "flashplayer-installer: command not found"

Interesting. I forgot to add a "/". I can help you from here tho. Just paste the following to finish:
```
cd /tmp/install_flash_player_9_linux; sudo ./flashplayer-installer
```

---

### Post by Stickymaddness on 2007-04-12
**The file does exist!**

```

wget http://stwww.weizmann.ac.il/G-CS/BENARI/files/frogs.swf
--00:13:33--  http://stwww.weizmann.ac.il/G-CS/BENARI/files/frogs.swf
           => `frogs.swf'
Resolving stwww.weizmann.ac.il... 132.77.150.101
Connecting to stwww.weizmann.ac.il|132.77.150.101|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 61,967 (61K) [application/x-shockwave-flash]

100%[====================================>] 61,967        --.--K/s             

00:13:34 (422.04 KB/s) - `frogs.swf' saved [61967/61967]

```

I've included a screenshot from firefox, as you can see, it's clearly there!

---

### Post by x-ray vision on 2007-04-12
> **bashologist said:**
> Interesting. I forgot to add a "/". I can help you from here tho. Just paste the following to finish:
```
cd /tmp/install_flash_player_9_linux; sudo ./flashplayer-installer
```

What do I type in when I get to the part that asks: 

Please enter the installation path of the Mozilla, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla): 
dir= /tmp/install_flash_player_9_linux/

---

### Post by bashologist on 2007-04-12
> **x-ray vision said:**
> What do I type in when I get to the part that asks: 

Please enter the installation path of the Mozilla, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla): 
dir= /tmp/install_flash_player_9_linux/

Hrm... using sudo should be able to install system wide somehow. I'm not sure what to do at that point to do that tho.

Exit the script with "ctrl+c", then type the following:
cd /tmp/install_flash_player_9_linux; ./flashplayer-installer
# Then press "enter" for the first prompt.
# Then "Enter" again.
# Then "y".
# Then "n".

The little script I made wasn't so good I guess.

---

### Post by x-ray vision on 2007-04-12
> **bashologist said:**
> Hrm... using sudo should be able to install system wide somehow. I'm not sure what to do at that point to do that tho.

Exit the script with "ctrl+c", then type the following:
cd /tmp/install_flash_player_9_linux; ./flashplayer-installer
# Then press "enter" for the first prompt.
# Then "Enter" again.
# Then "y".
# Then "n".

The little script I made wasn't so good I guess.
I did the above and the link you gave me still doesn't work. I also got this message after it installed:

[b]NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.[/b]

What's that all about?

---

### Post by bashologist on 2007-04-12
> **x-ray vision said:**
> I did the above and the link you gave me still doesn't work. I also got this message after it installed:

[b]NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.[/b]

What's that all about?

I've never seen this message. Maybe you had a web browser open when you went through the installer?

Used google and found this:
[http://www.linuxquestions.org/questions/showthread.php?p=2703504](http://www.linuxquestions.org/questions/showthread.php?p=2703504)

I don't know. That's how I installed flash. I can't help any more than that.

---

### Post by x-ray vision on 2007-04-12
Does anyone know how I can delete the xpti.dat file? 

The link that bashologist posted had a reply from someone that after he deleted it, the flash player worked.

---

### Post by bashologist on 2007-04-12
Ok, this is the last step in my 999 step tutorial. n_n

Maybe this will help you locate the file:
```
which xpti.dat
locate xpti.dat
```

---

### Post by x-ray vision on 2007-04-12
I don't know what you're telling me to do.

---

