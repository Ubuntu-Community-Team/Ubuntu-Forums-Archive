---
title: "make directory and change permissions"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Elf on horseback on 2007-07-23
I am trying to install

---

### Post by Foxmike on 2007-07-23
> **Elf on horseback said:**
> I am trying to install
Great and welcome!
 
What is your question?

---

### Post by Elf on horseback on 2007-07-23
I hate when i post like that by mistake, sorry.

the problem is right now i am trying to install Mozilla Composer for linux.  Install always stops at making the Mozilla directory.  I tried to go and move a folder named Mozilla from the desktop in to /user/local/.  sadly that did not work either.  i get the error message 
```
Error while copying to "/usr/local".
You do not have permissions to write to this folder.
```
Any ideas what I should do?

---

### Post by asmoore82 on 2007-07-23
if you really know what you are doing you can install the software as root ...
a good 21st century safer solution would be installing the software without special permission; i.e. in your home folder ...  $HOME/local/

if you are compiling from source, the time to choose where to install is at the ./configure stage ...
```
src $ ./configure --prefix=$HOME/local
```

---

### Post by Foxmike on 2007-07-23
In order to install something under Linux, you need administrator's privileges.  If you are sure of what you are doing (your script is safe, the softwares comes from a secure source) then you can tipe in the command line (terminal)
```
sudo <insert-here-the-path/name-to-the-script/installer
```
It will execute the installer with administrator's privileges and then will be able to create the /usr/local/Mozilla folder.
 
Have you tried to install Composer thru Synaptics?  (I don't know if it is in there).

---

### Post by Elf on horseback on 2007-07-23
i looked for Mozilla Composer in Synaptics, nothing. the folder i need to install to is /usr/local/mozilla.

What I am really trying to find is a WYSIWYG HTML editor.   I have searched about WYSIWYG and all that comes up is nVu (not being dev any more), Bluefish (NOT a WYSIWYG), and Mozilla Composer.  I am really trying to find a program like Dreamweaver but in linux.  I would like to avoid using Wine if i can.

---

### Post by Nythain on 2007-07-23
ok, a few solutions to this problem
A. if you are running an installer (usually something like install.sh or whatnot) just use sudo in front of it
B. if you are manually compiling and making it to the make install phase of the installation, be sure to use sudo
C. if you want to continue with this idea of just making the folder and copying it over yourself (wich probably isnt going to work because its going to want to put files in the folder, so again you will have permission problems) you can copy the folder over by typing this in terminal
```

sudo cp ~/Desktop/Mozilla /usr/local/Mozilla

```
but like i said, that solution NOT recomended... you should first try running the part you are getting stuck at with sudo

---

### Post by asmoore82 on 2007-07-23
IMHO ... there can be only 1 html/xhtml editor ... Amaya, from the W3C itself ... available thru apt/synaptic

---

### Post by Elf on horseback on 2007-07-23
to do the terminal install do i need to get to the file some where like yo did in dos.  like c://windows/syster32 then punch in the comand or can i run the install from anywhere

---

### Post by Foxmike on 2007-07-23
> to do the terminal install do i need to get to the file some where like yo did in dos. like c://windows/syster32 then punch in the comand or can i run the install from anywhere
You can just leave the file where it is wright know.  Make sure it is executable by doing in the terminal:
```
chmod u+x <name-of-the-file-here>
```
and then:
```
sudo <name-of-the-file-here>
```
to execute it.  Again, make sure the file you want to execute comes from a trusted source.  I you don't want to get a security flaw in your system.

Regards,

-FM

---

