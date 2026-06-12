---
title: "Matlab 2007a installed but having problems running it"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by pipa on 2007-11-30
Hi guys,
I am new to this forum and new to linux too.
I followed Matlab instructions to install MATLAB 2007a. When I type "matlab" on command line, I get the following error. 

License checkout failed.
License Manager Error -15
MATLAB is unable to connect to the license server. 
Check that the license manager has been started, and that the MATLAB client machine can communicate
with the license server.

Troubleshoot this issue by visiting: 
[http://www.mathworks.com/support/lme15a](http://www.mathworks.com/support/lme15a)

Diagnostic Information:
Feature: MATLAB 
License path: /usr/local/matlab74/etc/license.dat:/usr/local/matlab74/etc/*.lic: 
FLEXnet Licensing error: -15,570. System Error: 115


Does anybdy know why I am getting this error and how to address this error.

Thanks
pipa

---

### Post by bukwirm on 2007-11-30
It appears that MATLAB could not connect to a server to get you a license. Since I haven't tried to use MATLAB on Linux, I can't make any specific suggestions yet.

Can you post the instructions you followed?

If you don't need any of MATLAB's more exotic features, you could try octave, which is nearly compatible. It should be in the repositories.

---

### Post by pipa on 2007-11-30
Thanks for ur reply.
I pretty much followed the instructions mentioned in the installation document provided by MATLAB.
I copied my licence file in the directory where I wanted to install MATLAB (/usr/loca/MATLA74).I followed pretty much all the steps. I got some erros for lmstart also, which I couldn't figure out. 
After that , whenever I type matlab, I get the above mentioned error segment.

Thanks.
pipa

---

### Post by Whiffle on 2007-11-30
What did you name hte license file?  I think it has to be like license.dat or something

---

### Post by pipa on 2007-11-30
> **Whiffle said:**
> What did you name hte license file?  I think it has to be like license.dat or something

Yes, I renamed it to licence.dat.

---

### Post by dracker on 2007-11-30
I used Matlab 2006b in ubuntu,the instructions to run it was first to run the Matlab server daemon and then Matlab itself, maybe 2007a is just the same.
Sorry but I don't have the console command... but search for it in the manual.

---

### Post by pipa on 2007-12-01
Yeah thats correct. I think its called lmstart. I tried running it but I still got some errors.
I will post the errors I got shortly.
Thanks guys
pipa

---

### Post by pipa on 2007-12-04
I think I figured out the problem. There were few lines missing from my licence.dat file.
Matlab now starts but the editor window is grayed out and I can't see anything. 
However when I turn off the GL Desktop effects, everything works fine. Does anybdy know how to get rid of this problem. I want my GL Desktop to be turned on.

Thanks.
Pipa

---

### Post by syxbit on 2007-12-04
2007b is out now!, you should upgrade
i tried installing it, and i think it worked, however it doesn't seem like the windows version
i loaded it up (installed it today) and i get a grey window with a start button at the buttom left.
what happened to the regular window where you can type expressions in?

---

### Post by AegisTalons on 2007-12-04
Ok, got it. Just needed to:
1. Add the following line (before the first uncommented one) to Matlabdir/bin/matlab


```
export AWT_TOOLKIT=MToolkit
```

to
2. Launch matlab

```
matlab -desktop
```

It runs from the Launch app menu (Alt+F2).

If that doesn't work for you then you may need to do rename a java directory in the MatLab install.

Hope that helps.

---

### Post by pipa on 2007-12-05
Thanks I will try that out.

---

### Post by pipa on 2007-12-10
WOW!!

That WORKS!!!!!

Cool, Thanks.
PIPA

---

### Post by frecon on 2007-12-13
Thank you!

I can now (finally) start working with matlab. :)

---

### Post by amightyo on 2007-12-17
Thanks so much. It also worked for me. Guess I will soon be out of Windows:) and full on Ubuntu

---

### Post by jmarcos on 2007-12-18
I am having a different problem... The installation was just fine, but whem I try to run I recieve the message: 
*** glibc detected *** /usr/local/matlab7/bin/glnxa64/MATLAB: malloc(): memory corruption: 0x0000000000598070 ***


Do anyone knows what is wrong ????
Thanks

---

### Post by stellar on 2007-12-20
Pipa,

Could you please let me know how did you resolve this issue - 

"License Manager Error -15
MATLAB is unable to connect to the license server."

Thanks!

---

### Post by AegisTalons on 2008-04-06
That looks like a MatLab licensing issue. When I installed MatLab. Before I even started the installer. I did the following.

Under terminal:
1) sudo mkdir /opt/matlab/
2) sudo cp license.dat /opt/matlab/license.dat

Regarding the second step, you want to copy the license file you have to the install directory ("/opt/matlab/") in my case.

Then I ran the installer by CDing into the directory and running ./install.

Mine is setup as a locked node, which means it does not need to connect to a license server or have to have a license server running to run it.

Hope that helps.

---

