---
title: "Codecs?"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by sjason2007 on 2006-08-20
how do i get .mpg files to work?
the sould works but not the video.
could some one please tell me how to get it to work step by step, i have no idea what i am doing.
i have had ubuntu for about 3 days

---

### Post by nalmeth on 2006-08-20
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

In case you're not sure where to paste commands, go Applications - Accessories - Terminal. The instructions are:
wget [http://easyubuntu.freecontrib.org/files/easyubuntu-3.022.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.022.tar.gz)
tar -zxf easyubuntu-3.022.tar.gz
cd easyubuntu
sudo python easyubuntu.incopy and paste each command one by one.

---

### Post by loserboy on 2006-08-20
have you tried using automatix?

[www.getautomatix.com](www.getautomatix.com)

pretty self explanitory but it will set alot of crap up for you, its the first thing i do after updating when i build a system

Edit: oh sorry the above post wasnt there when i started making this post.... but for the record i like automatix

---

### Post by sjason2007 on 2006-08-20
i typed what you said but it says that there is no such directory.
what does tht mean?
did i need to extract the foles i downloaded?
what should i do now?

---

### Post by sjason2007 on 2006-08-20
there is an error message, how do i fix "broken packages"?

---

### Post by nalmeth on 2006-08-20
Sorry, I did see what I posted, it may have caused things to go wrong:
```
 wget [http://easyubuntu.freecontrib.org/files/easyubuntu-3.022.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.022.tar.gz)
tar -zxf easyubuntu-3.022.tar.gz
cd easyubuntu
sudo python easyubuntu.in
```

Copy and paste these lines..

Where are you getting the directory not found? I'm guessing the last command? 
Try it again as you see it now.

For the record, I've long recommended automatix, but thought I'd try Easy Ubuntu for a while..
Odd, the instructions aren't as "easy" as they could be

Edit: to fix broken packages/dependencies, use this command:
```
 sudo apt-get -f install
```

Also, this command:
tar -zxf easyubuntu-3.022.tar.gz
Is used for extracting the archive containing easy ubuntu. You can do it graphically, but since you're in the terminal anyway, it should be easier to use the command.

Sorry for any confusion :???:

---

### Post by sjason2007 on 2006-08-20
when i type the command to fix broken packages it says it upgrades and fixes none of the files, what should i do?
is also says that some have already been installed and easyubuntu can not uninstall them. can i uninstall those somehow?

---

### Post by nalmeth on 2006-08-20
Can you post the output of:
```
sudo apt-get update
sudo apt-get -f install
```
Sorry about this mate, hopefully I can help sort it out

Did easyubuntu actually run?

---

### Post by sjason2007 on 2006-08-20
yes east ubuntu runs but then closes b/c of the packages being broken

---

### Post by nalmeth on 2006-08-20
Run:
```
sudo apt-get update
``` 
Post the output of:
[LEFT]```
 sudo apt-get -f install
```
The page detailing how to manually install codecs is here:
[http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)
[/LEFT]

---

### Post by sjason2007 on 2006-08-20
do i need to open a new terminal to type in the commands or do i type them in one after the other?
for the updates where do i type them?
the first one worked but the second one did not.
there were no updates, or anything, fwhat should i do?
when the easy ubuntu runs there are things alreasy installed. 
how would i uninstall those, and which boxes should i check?
there are only four that i can check

---

### Post by nalmeth on 2006-08-21
Just one command after the other.
Exactly what does the terminal tell you after running
```
sudo apt-get -f install
```
Copy what it says and paste it here

I'm not sure exactly how/what Easy Ubuntu installs and in what order.. Is there a log/text file in the easyubuntu folder, or in your home folder, or desktop?

Again, to manually install the codecs, or uninstall them check here:
[http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)

sudo apt-get install package_name
sudo apt-get remove package_name

hopefully this helps

---

### Post by sjason2007 on 2006-08-21
this is so complicated
i think i will try and find someone that can do it for me at school.....
thanks for the help though

---

### Post by nalmeth on 2006-08-21
I'm sorry dude, one little typo and things just ran off.

If you can't find any help at school, PM me, and thru messenger or something I will help you out. 

The output of that command is quite important, and this mess really shouldn't be hard to clear up. 

Maybe I should just go back to recommending automatix :p (j/k E.U. devs)

---

### Post by loserboy on 2006-08-21
> Maybe I should just go back to recommending automatix

*cough told ya so cough*

jk

---

