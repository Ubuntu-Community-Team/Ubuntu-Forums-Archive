---
title: "Firefox + Digg = 100% Processor Use...so slow.."
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by gmc1200 on 2007-01-13
Hey im semi-new to ubuntu andI'm having some trouble.  I'm an on/off ubuntu user, the reason for that is situations like this. 

 I was having trouble with the choppy scolling with firefox while on digg.com, but I managed to make that go away by manually installing the nvidia driver.  Before, i would just use automatix2 to install the driver, but everytime, i would have the same problem.  so im just glad im not experiencing problems with that anymore.

But now, whenever I'm on digg.com and i click new links or open them up in new tags, the cpu spikes and my whole computer becomes extremely sluggish.  this is especially aggravating when listening to music or watching videos and so on.  

I really want to keep ubuntu as my main os, but this issue is extremely annoying.  digg and engadget are websites that have this problem, more digg than engadget.  otherwise, its perfectly fine.  The weird thing is i don't remember the sluggish behavior occurring before in the past on my computer.  Ive installed edgy when it came out and then switched back and forth from windows from then on and it was fine for a while, so i guess this has been happening for the past 2-3 months.  

My computer specs:

p4 2.4ghz
1gb ram
nvidia mx440 64mb


If anyone has input it would be appreciated!!!

---

### Post by shash_walia on 2007-01-13
im new to ubuntu acutally. but i think i might have a solution for you. what you can try and do is that open your browsers and music applications on different desktops.As you would be knowing that ubuntu offers different desktops (default of 4) to choose from.

try that and see how it gows 

best of luck

---

### Post by gmc1200 on 2007-01-13
I tried this out, but it didnt work.  If anyone else has any suggestions, please post!!

---

### Post by confused57 on 2007-01-13
If you haven't already, you might want to install the "NoScript" and "AdBlock" extensions in Firefox, especially NoScript.
NoScript allows you to select whether to allow JavaScript or not for the site you're visiting.

---

### Post by Tomosaur on 2007-01-13
Is this when you click on an actual digg page, or when you click FROM digg to a story or different website?

---

### Post by Colonel Kilkenny on 2007-01-13
Digg uses quite much Javascript and that might be the reason why it is slow in Firefox. I'm not using Firefox, but I've heard complaints about Firefox + sites which use heavily scripting.

So if Javascript is the problem disable scripting or try other browsers (Opera, Konqueror, etc (Epiphany and others using Gecko might have exactly same problems as Firefox))

---

### Post by gmc1200 on 2007-01-13
It happens when i click links within the digg site, not sites external from digg.  so if want to go to the technology section, look at comments, etc... it lags like crazy.

i tried out noscript and disabling it, no difference.  i think its weird that im having this problem, im sure there are plenty of people out there that arent having this problem.

i did manage to fix it by using opera, but i prefer using firefox.  so im content right now:-D , but if anyone knows any solution to this please let me know.

thanks again!

---

### Post by jpeddicord on 2007-01-13
Clicking on stories in a new tab with lots of comments tends to cause a CPU usage spike. The best thing to do is let the page(s) load fully and then CPU usage will be normal.

Digg overloads their pages with JavaScript. ](*,)

---

### Post by gmc1200 on 2007-01-13
but i think it weird because it works perfectly fine now in opera and im sure there are people out there not experiencing this problem, im just baffled on why it does that:confused:

---

### Post by Chris Allison on 2007-01-14
I am almost certain that I have this same problem.  The problem occurs at digg.com and engadget.com as you mentioned, and possibly other sites.  I have narrowed the problem down.  It appears that an image that digg.com is loading is causing the problem.  I do not know why the  problem only occurs for a very few number of people.  Please use the following work-around in Firefox to eliminate the problem:

- Go to: Edit -> Preferences -> Content.
- Click Exceptions... next to Load images automatically.
- Add digg.com so it is blocked.
- Go to digg.com and test.

The obvious negative side-effect of the workaround is that you will not be able to see any images at digg.com, but the site should still be usable.

I wonder which image(s) is causing the problem and why?  Could it be a background image that is trying to tile too many times?  If so, why does it only affect us?

As you reported, this problem only started happening to me about 1-3 months ago.  It started happening sometime after I upgraded to Edgy Eft.  I am not sure if it started right after I upgraded or not.

---

### Post by globexispower on 2007-03-06
I have been having this same problem.  I read somewhere that it was a video driver issue...i forget where so I don't have the link.  But i installed the newest version of the NVIDIA drivers from there site and now the page loads fast.

I have an NVIDIA GeForce 6800 XT, here is what I did:
1. Download the newest drivers from [http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html") to you desktop
2. After the download finishes stop the X windows server with
```
sudo /etc/init.d/gdm stop
```
3. In the terminal navigate to your Desktop and run the script with
```
sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run 
``` (NVIDIA-Linux-x86-1.0-9746-pkg1.run being the name of the file downloaded from the nvidia site)
4. Follow the onscreen instructions and restart X with
```
sudo /etc/init.d/gdm start
```

After this I went to engadget which used to take over 1 min to load and now it loads in less then 10 secs.

---

### Post by stormrider on 2007-04-17
Quick follow-up.
I had this same problem with Fiesty beta, firefox 2.0 and default video drivers. Once I'd installed nvidia drivers through Automatix everything worked fine.
Graphics card: Geforce Ti200

---

### Post by daradib on 2007-04-18
Same problem here. Using Feisty Beta on ATI Radeon card (with ati open source driver, NOT fglrx). This problem is new, I didn't always have it when I first got Feisty (either Herd 5 or Beta).

By checking another thread, it seems the issue might be digg.com/img/main-back.gif which I will try blocking and report my results.

Another site has said that the problem is with Firefox rendering transparent PNG's in a way that would require 3D rendering (Although I have 3D according to glxinfo, there are some issues when I move windows around and when using Beryl.

Check out this site and see what happens when it loads:
[http://www.linuxactionshow.com](http://www.linuxactionshow.com)
I get a slight slowdown, but definitely not as bad as Digg.

Finally, see this bug report:
[https://bugzilla.mozilla.org/show_bug.cgi?id=328319](https://bugzilla.mozilla.org/show_bug.cgi?id=328319)

EDIT: Blocking digg.com/img/main-back.gif in Adblock Plus seems to have solved my problem.

---

### Post by medya on 2007-04-25
I have the same problem !

---

### Post by medya on 2007-04-25
read this blog post [to fix the problem ]("http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html")

---

### Post by Yellow Onion on 2007-05-09
Im have similar Problems firefox gets really slow on pages with opacity/transparent objects (eg div's tables pngs) CPU spikes to 100% every time i scroll down
I have a ATI X800XL
glxinfo reports direct rendering = yes
Doom 3 runs fine
and firefox in windows renders these pages fine no lag
does firefox/linux use a different rendering system than firefox/windows?
or is there some config i can change?
or is there a way of disabling opacity/transparency?

---

