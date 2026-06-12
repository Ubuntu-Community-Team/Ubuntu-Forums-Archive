---
title: "A little help with a wine bug please.."
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Saulie on 2007-08-20
Heya guys I am getting a message saying 'unable to intalize vbox' when I load up photoshop 7 on wine. however I have found it as a bug on the wine site and it has been fixed.

[http://bugs.winehq.org/show_bug.cgi?id=4635](http://bugs.winehq.org/show_bug.cgi?id=4635)

I don't understand how to fix it, could anybody please explain to me how to fix it? 

Thanks in advance, saulie.

---

### Post by raijinsetsu on 2007-08-20
You might have to update your wine...
Try running "apt-get update" then "apt-get install wine".

---

### Post by jakev383 on 2007-08-20
It may be fixed on the Wine site, but the version you installed from the repos (I'm assuming you used Aptitude or apt-get to install it) may be a few versions behind.  You could try installing the source version and see if that resolves the issue.

---

### Post by Saulie on 2007-08-20
I just installed wine two days and i downloaded the latest version from their site.

---

### Post by raijinsetsu on 2007-08-20
type "wine -v" and check the version that way.

---

### Post by Saulie on 2007-08-20
> **raijinsetsu said:**
> You might have to update your wine...
Try running "apt-get update" then "apt-get install wine".

I got a message saying that I had the latest version when i tried them.

---

### Post by raijinsetsu on 2007-08-20
I don't know then. Have you tried the Wine forums?

---

### Post by mikeyphi on 2007-08-20
> **Saulie said:**
> Heya guys I am getting a message saying 'unable to intalize vbox' when I load up photoshop 7 on wine. however I have found it as a bug on the wine site and it has been fixed.

[http://bugs.winehq.org/show_bug.cgi?id=4635](http://bugs.winehq.org/show_bug.cgi?id=4635)

I don't understand how to fix it, could anybody please explain to me how to fix it? 

Thanks in advance, saulie.


I think this is the patch you are looking for!
[http://www.winehq.org/pipermail/wine-patches/attachments/20070427/20fbc301/ps7.bin](http://www.winehq.org/pipermail/wine-patches/attachments/20070427/20fbc301/ps7.bin)

---

### Post by Saulie on 2007-08-20
> **mikeyphi said:**
> I think this is the patch you are looking for!
[http://www.winehq.org/pipermail/wine-patches/attachments/20070427/20fbc301/ps7.bin](http://www.winehq.org/pipermail/wine-patches/attachments/20070427/20fbc301/ps7.bin)

I have opened it through wine file and got a message saying success however when i load up photoshop 7 I still get the same unable to initialize vbox message. Am I not running the patch correctly or something? I found it through wine file and double clicked it.

---

### Post by Saulie on 2007-08-20
Guys don't leave me hanging please =(

---

### Post by Saulie on 2007-08-20
Anyone? =(

---

### Post by Saulie on 2007-08-20
I know this is lame but I will give $5 over paypal to anyone who can solve this for me. I have client work that I need to finish and gimp wont let me edit psd layers so i need photoshop really badly.

Cheers, Saulie.

---

### Post by mysticmatrix on 2007-08-20
Since you are ready to pay, why don't you try Crossover for professional wine solution????

Get the trial version and quit complaining.

[www.codeweavers.com](www.codeweavers.com)

---

### Post by jakev383 on 2007-08-22
> **Saulie said:**
> I know this is lame but I will give $5 over paypal to anyone who can solve this for me. I have client work that I need to finish and gimp wont let me edit psd layers so i need photoshop really badly.

Cheers, Saulie.

I'd make a post over in the wine forums.  I personally don't use it (VMWare here), so I can't offer much help.  Remember that wine is still not finished, so bugs/fixes come out often.

---

### Post by Brightbelt on 2007-08-22
Despite Mysticmatrix's poor bedside manner, I do agree with him. CrossOver is a good program in my opinion - it costs only $39.95 (I think)  - and I think it makes significant improvements over wine in running PS 7.0. 

I know firsthand because I tried both wine and CrossOver with PS 7.0 myself. CrossOver does a much better job period. And like he mentioned, you can try the trial version for free.

It's definitely worth the money I think. And the money you pay for CrossOver actually goes into helping to improve the Wine program, which benefits everybody. So you're actually supporting a good cause at the same time.  

Good Luck. ;)

---

