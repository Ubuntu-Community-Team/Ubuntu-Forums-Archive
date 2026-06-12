---
title: "PlayOnLinux - Scripts within PlayOnLinux"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by Sugi on 2008-02-16
How do I use scripts within PlayOnLinux?  I go to their website and load the page with the script.  Then what?  Within PlayOnLinux, I go Tools > Run non-offical Script and then I browse for the script.  But I do not know how get the script off the website and into PlayOnLinux.  I have tired coping the script from webpage into gedit and saving it as file.sh.  Then, I try opening it up in PlayOnLinux, but it says the format is incorrent.  Then, I try just saving it as "oblivion" no file format after the name, so it goes into native format, but still the same thing not a valid format for PlayonLinux.  What should I do?

Oblivion script for PlayOnLinux [http://www.playonlinux.com/en/script-47.html]("http://www.playonlinux.com/en/script-47.html")

Sugi

---

### Post by yabbadabbadont on 2008-02-17
I don't know if it will work for you (it doesn't look like a normal bash script to me), but here you go.

---

### Post by Sugi on 2008-02-19
I'll give it a try, but I don't think it's what I am looking for.

BUMP

---

### Post by yabbadabbadont on 2008-02-19
> **Sugi said:**
> I'll give it a try, but I don't think it's what I am looking for.

BUMP

It is the script from the page to which you linked....  if it isn't what you are looking for, then why did you provide a link to it?  :lol:

---

### Post by Sugi on 2008-02-20
I'm sorry, I didn't know you made script file out of the oblivion script.  How did you make the script.  Because I tired making a script for PlayOnLinux in the format of .sh and PlayOnLinux didn't take it.

---

### Post by seventhc on 2008-02-20
Is this something you run through wine? 
```

Ask_For_cdrom 
Check_cdrom "setup.exe" 

mkdir -p $REPERTOIRE/wineprefix/ElderScroll4_Oblivion 
cd $REPERTOIRE/wineprefix/ElderScroll4_Oblivion 
select_prefixe "$(pwd)" 
creer_prefixe 

cd $WINEPREFIX/drive_c/windows/ 
mkdir temp 
cd $WINEPREFIX/dosdevices 

```

---

### Post by Sugi on 2008-02-21
Yes, then it runs through PlayOnLinux.
[playonlinux.com]("www.playonlinux.com")


What do I do with that code?  Make a script out of it or just input it into the terminal?
> Ask_For_cdrom 
Check_cdrom "setup.exe" 

mkdir -p $REPERTOIRE/wineprefix/ElderScroll4_Oblivion 
cd $REPERTOIRE/wineprefix/ElderScroll4_Oblivion 
select_prefixe "$(pwd)" 
creer_prefixe 

cd $WINEPREFIX/drive_c/windows/ 
mkdir temp 
cd $WINEPREFIX/dosdevices

Sugi

---

### Post by seventhc on 2008-02-21
thats just a part of the code that was from the link provided by you.

---

### Post by Sugi on 2008-02-21
I am still really new to scripts.  I don't even know what to do with the script-file.sh.  I don't understand them yet.

Sugi

---

### Post by seventhc on 2008-02-21
well, a normal script you would save it as name.sh then open a terminal and run this
```

chmod a+x name.sh              ( chmod +x name.sh works too )
chmod 755 name.sh

```
the above code explained
 first command - makes it executable
 second command - gives it permissions

Then to run it you would open a terminal and do this
```

./name.sh

```The above command would normally run the script,
but I don't know about this one since wine is involved.

I don't even know what PlayOnLinux is. :confused:

---

### Post by Sugi on 2008-02-21
> $ chmod a+x name.sh
$ chmod 755 name.sh

Could you explain why I do "$ chmod a+x name.sh" and then "$ chmod 755 name.sh"?  I would like to know the gears works behind the terminal command lines.

Sugi

---

### Post by seventhc on 2008-02-21
A sample useless hello world.
Open gedit and type
```
echo 'Hello World!'

```
save it as hello.sh
then open a terminal and put
```

chmod +x hello.sh

```
This doesn't need permissions so I didn't use the 755.
Now if you use the same terminal or close it and reopen it type
```

./hello.sh

```
and it should say [COLOR=DarkGreen]Hello World![/COLOR]

---

### Post by seventhc on 2008-02-21
I did explain it, it's in the post.
but here it is again
chmod +x      *will make it executable* 
chmod 755    *[COLOR=Black]gives it permissions[/COLOR]*

---

### Post by Sugi on 2008-02-22
> chmod 755 gives it permissions
Does it give it permissions to ron?

Sugi

---

### Post by seventhc on 2008-02-22
Who's *ron*??? 
It depends on what permission you want *ron* to have and if thats a separate user or the owner of the file. If *ron* is a second user but not the owner of the file then *ron* would be able to *read*, and *execute* but not *write*.
To make it easier to understand, here is a permissions calculator which might help put it into perspective.

[http://www.robolink.co.uk/calculators10.htm](http://www.robolink.co.uk/calculators10.htm)
 You can change the number according to what permissions you want *ron* to have.

and some more info here
[http://www.linuxforums.org/security/file_permissions.html](http://www.linuxforums.org/security/file_permissions.html)

---

### Post by Sugi on 2008-02-22
Nevermind.  Sorry, I read something on the forums and I got confused.  I don't have a user named ron.  >.<  Thanks for the links though.  I think, though, it has nothing to do with PlayOnLinux, because I need to run the script through PlayOnLinux.  It does all the terminal work for me, but I just don't know what format it needs for the program.

Sugi

---

