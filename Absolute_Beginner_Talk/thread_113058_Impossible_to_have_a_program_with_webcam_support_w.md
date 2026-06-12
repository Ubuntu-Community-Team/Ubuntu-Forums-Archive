---
title: "Impossible to have a program with webcam support with Linux ?"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-01-05
Kopete doesnt accept webcam support by default install: 
```
apt-get -f install kopete
```
  
is there a easy way to make it ?
  
Kind regards, 

Pat'

---

### Post by Sef on 2006-01-05
I don't think that it will have webcam support till KDE 4.0.  However, amsn does have some webcam support.  It is in the respositories, so either download it with Synaptic (System -----> Administration --------> Synaptic Package Manager and do a search for it) or with apt-get (Open terminal ----> sudo apt-get install amsn.)

---

### Post by patrick295767 on 2006-01-06
[QUOTE=Sef]I don't think that it will have webcam support till KDE 4.0.  However, amsn does have some webcam support.  It is in the respositories, so either download it with Synaptic (System -----> Administration --------> Synaptic Package Manager and do a search for it) or with apt-get (Open terminal ----> sudo apt-get install amsn.)[/QUOTE]
  
I tried with the sources.list
but when u do 
```
apt-get -f install amsn
```
  
U get an old version of amsn wihtout any webcam support ... 
 
Please could you copy in this thread your /etc/apt/sources.list that is having the amsn with webcam support ?
  
Thank you very much !!
  
Patrick

---

### Post by lex on 2006-01-06
[QUOTE=patrick295767]I tried with the sources.list
but when u do 
```
apt-get -f install amsn
```
  
U get an old version of amsn wihtout any webcam support ... 
 
Please could you copy in this thread your /etc/apt/sources.list that is having the amsn with webcam support ?
  
Thank you very much !!
  
Patrick[/QUOTE]




I'm trying to install amsn to i did get the old version from the sources.list. But I'd like to know how to install the newer version. I'm a total newbie. Could you please advise?
Thanks
Lex

---

### Post by meborc on 2006-01-06
try this thread [http://ubuntuforums.org/showthread.php?t=102299](http://ubuntuforums.org/showthread.php?t=102299) ... it is a guide by gandalf how-to install amsn...

---

### Post by patrick295767 on 2006-01-06
```

```[QUOTE=lex]I'm trying to install amsn to i did get the old version from the sources.list. But I'd like to know how to install the newer version. I'm a total newbie. Could you please advise?
Thanks
Lex[/QUOTE]
  
To install amsn (I already did it (the last version )) on another pc):
```
apt-get -f install amsn 
```
  
then u have libs and old amsn
to upgrade it now:
go : 
dopwnload the autopackage:
[http://prdownloads.sourceforge.net/amsn/amsn-0.95.x86.package](http://prdownloads.sourceforge.net/amsn/amsn-0.95.x86.package)
  
```
chmod +x amsn-0.95.x86.package
```
  
then : 
```
./amsn-0.95.x86.package
```
  
Now it's isntalled and upgraded to 0.95 :-)
  
And let's pray, it works !
  
Please let me know the result !
  
Pat'

---

### Post by patrick295767 on 2006-01-06
[QUOTE=lex]I'm trying to install amsn to i did get the old version from the sources.list. But I'd like to know how to install the newer version. I'm a total newbie. Could you please advise?
Thanks
Lex[/QUOTE]
 
And, did you try this [http://ubuntuforums.org/showthread.php?t=102299](http://ubuntuforums.org/showthread.php?t=102299) ?
  
Let me know the workign one with webcam support please ... 

Greetings

---

### Post by lex on 2006-01-06
[QUOTE=patrick295767]```

```
  
To install amsn (I already did it (the last version )) on another pc):
```
apt-get -f install amsn 
```
  
then u have libs and old amsn
to upgrade it now:
go : 
dopwnload the autopackage:
[http://prdownloads.sourceforge.net/amsn/amsn-0.95.x86.package](http://prdownloads.sourceforge.net/amsn/amsn-0.95.x86.package)
  
```
chmod +x amsn-0.95.x86.package
```
  
then : 
```
./amsn-0.95.x86.package
```


  
Now it's isntalled and upgraded to 0.95 :-)
  
And let's pray, it works !
  
Please let me know the result !
  
Pat'[/QUOTE]



Thought it was to easy. I got this message after following instructions "The following package was successfully installed:
 &#8226; AMSN MSN client":D 
But then when i tried to open it "[COLOR="Blue"]You can't load TkCximage, this is now needed to run aMSN. Please compile amsn first, instruction on how to compile are located in the file INSTALL[/COLOR]" 
Where do I find this and is compiling hard? Dont even know what it means?
I'm getting there though.
Thanks for your help.
Lex

---

### Post by lex on 2006-01-06
Just found this message, "Autopackage support code was installed.
Autopackage graphical interface was installed.

# # # # # # # # # # # #

Thank you for your patience. Installation of your package will now proceed.
You should not have to install the autopackage support code again.

# # # # # # # # # # # #

In file "/usr/lib/menu/amsn", at (or in the definition that ends at) line 4:
[...]n="msn.png" longtitle="\"MSN Messenger for Linux"" kde_opt="X-Autopackage=@amsn.sourceforge.net/amsn:0.95\\nEncoding=UTF-8\\nInfo=AMSN\\nComment[fr]=\"MSN Messenger pour Linux"\\nComment[de]=\"MSN Messenger fr Linux"\\nComment[nl]=\"MSN Messenger voor Linux"\\nComment[no]=\"MSN Messenger for Linux"\\nTerminal=false\\nType=Application\\n"
[...]                                                 ^
Expected: "="
Skipping file because of errors...

lex@ubuntu:~$"

something failed.

---

### Post by patrick295767 on 2006-01-06
[QUOTE=lex]Thought it was to easy. I got this message after following instructions "The following package was successfully installed:
 • AMSN MSN client":D 
But then when i tried to open it "[COLOR="Blue"]You can't load TkCximage, this is now needed to run aMSN. Please compile amsn first, instruction on how to compile are located in the file INSTALL[/COLOR]" 
Where do I find this and is compiling hard? Dont even know what it means?
I'm getting there though.
Thanks for your help.
Lex[/QUOTE] 
  
After that, I am blocked
very strange cos on my other PC, hoary, it's working !
I dont know which lib we need to install

---

### Post by patrick295767 on 2006-01-06
[QUOTE=lex]Just found this message, "Autopackage support code was installed.
Autopackage graphical interface was installed.

# # # # # # # # # # # #

Thank you for your patience. Installation of your package will now proceed.
You should not have to install the autopackage support code again.

# # # # # # # # # # # #

In file "/usr/lib/menu/amsn", at (or in the definition that ends at) line 4:
[...]n="msn.png" longtitle="\"MSN Messenger for Linux"" kde_opt="X-Autopackage=@amsn.sourceforge.net/amsn:0.95\\nEncoding=UTF-8\\nInfo=AMSN\\nComment[fr]=\"MSN Messenger pour Linux"\\nComment[de]=\"MSN Messenger fr Linux"\\nComment[nl]=\"MSN Messenger voor Linux"\\nComment[no]=\"MSN Messenger for Linux"\\nTerminal=false\\nType=Application\\n"
[...]                                                 ^
Expected: "="
Skipping file because of errors...

lex@ubuntu:~$"

something failed.[/QUOTE]
  
Thank you very much of ur nfo !!
Fast and accurate !
  
I'll had your pseudo in my buddy list to progress together in linux ! :-) 
  (I dont have my linux box pc for the moment... (tonight yes))

---

### Post by lex on 2006-01-06
[QUOTE=meborc]try this thread [http://ubuntuforums.org/showthread.php?t=102299](http://ubuntuforums.org/showthread.php?t=102299) ... it is a guide by gandalf how-to install amsn...[/QUOTE]


I've run this and it seens to be working a treat well heaps is going on in the termainal. lets hope it all works. Thanks everyone for your help.
gotta go now willpost to say if it work tomo.
Thanks again.
Lex

---

### Post by lex on 2006-01-06
IT WORKED. Yeah.
Thanks

---

### Post by lex on 2006-01-06
[QUOTE=patrick295767]Thank you very much of ur nfo !!
Fast and accurate !
  
I'll had your pseudo in my buddy list to progress together in linux ! :-) 
  (I dont have my linux box pc for the moment... (tonight yes))[/QUOTE]

Thanks that very kind of you! I look forward to your recomendation as I have no idea.
Lex

---

### Post by patrick295767 on 2006-01-06
[QUOTE=lex]Thanks that very kind of you! I look forward to your recomendation as I have no idea.
Lex[/QUOTE]
  
This is my progress thread: [http://www.ubuntuforums.org/showthread.php?t=64557&page=8]("http://www.ubuntuforums.org/showthread.php?t=64557&page=8")
I have to complete it now since I learned a lot more... 

I 'll try tonight to install amsn 0.95 as u said with the link...
  
Thank you again !
 
Patrick

---

