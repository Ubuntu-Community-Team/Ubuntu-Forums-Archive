---
title: "Xwine Or Wine??????????"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by phenix on 2006-03-26
I have been trying to install 'wine' in my G3 Pismo Power Book (500mhz, 640 ram) 
but all I can find in my repos is 'xwine', so I was wandering if that was what I needed to install. I have already tried following all of the different instructions provided in the winehq website and none of them work, and I also have all of the options possible enabled in my repositories, so I was wandering if there is somewhere that Im not looking or something Im not doing. 

Thank you guys!!!!!!!

---

### Post by wolfee on 2006-03-26
Ya forget about microshaft and find all your programs for ubuntu start with arnie boy's automatix!! I have it ant it's awesome!!!!!! anything windows can do linux can!! the problem with wine or any emulator is you use more cpu and ram to run a program from microshaft because you runwine and whatever so your running 2 programs 2x cpu and ram

---

### Post by gord on 2006-03-26
you should be able to add the wine hq's repository for debian/ubuntu on the winehq website [linky](http://www.winehq.com/site/download-deb). but if you have indeed tryed that and it has failed, i would suggest compiling wine yourself, download the source, do "sudo apt-get install build-essential bison" untar the source somewhere and follow the instructions in the readme. 

also, just to correct the person "wolfee", wine isn't an emulator in the traditional sence, it emulates the win32 api, so your win programs run as normal on linux, ie not requiring 2x cpu and ram.

---

### Post by wolfee on 2006-03-26
sorry I thought it was an emulator. I still say %^&* Microshaft and find everything via Linux.

---

### Post by jbmalone on 2006-03-26
Got rebels on the loose.

---

### Post by wolfee on 2006-03-26
[QUOTE=jbmalone]Got rebels on the loose.[/QUOTE]
Yup!!!!

---

### Post by phenix on 2006-03-27
sup guys thank all of you for your help so far.......
hey wolfee, I share your hate for 'microshaft', but still i think there are a few thing that I find usefull about them, and thats why I wanted to give wine a try....but automatix sounds pretty awesome so Im gonna look into getting it...

so gord, you said to run the command 'sudo apt-get build-essential bison'                            
what is the purpose of that command?..and can I just unpack the source file with any of the default utilities on ubuntu or should I do that through the command line..if so, I would like some tips on that, Im a complete beginner, and is a bit complicated but Im anxious to get this thing going...

thank you everybody!!!

---

### Post by Kryptizzle on 2006-03-27
The command is 'sudo apt-get install build-essential bison' :P. I think it's bascially like opening Synaptic, doing a search for build-essential and bison and installing it. You should be able to unpack the source by just opening it.

---

### Post by phenix on 2006-03-27
thanks Kryptizzle, I will try that...
man, thats was a dumb questions I asked. I was looking for 'build-essential bison' on my repos without taking in mind that there were two separate words....oh well, I never claimed to be  smart to begin with.

---

