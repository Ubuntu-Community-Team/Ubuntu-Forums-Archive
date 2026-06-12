---
title: "How to change what to type in terminal to run app"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by raul_ on 2006-09-16
Hey there. I installed the latest firefox manually, but now i have a problem. If i want to start the latest version, i have to type /firefox/firefox in the terminal (since i installed firefox in / ) but this is a pain in the a** . It's much easier to type simply "firefox" but that command is not recognized since i removed the prior version of firefox. I read something about changing the alias in ~/bashrc file or something like that but i don't know what to do exactly. Any ideas?
Thanks

---

### Post by x64Jimbo on 2006-09-16
Why are you launching from the command line anyway? Can't you just set up a desktop shortcut that runs /firefox/firefox?

---

### Post by raul_ on 2006-09-16
Lol. Sure i can. But that's not the point :)

---

### Post by picpak on 2006-09-16
Edit your .bashrc and put in

```
alias firefox='/firefox/firefox'
```

---

### Post by greyash99 on 2006-09-16
use ```

alias name of app
```
or just man alias to find out the proper way to do it
Edit:nvm got beaten to it

---

### Post by raul_ on 2006-09-16
Strange...it didn't work...even though i know what u said is correct =\ lol...oh well, i'll just stick to the /firefox/firefox thingy =(

thanks anyway guys =)

---

### Post by picpak on 2006-09-16
Did you try logging out and in?

---

### Post by raul_ on 2006-09-16
Loll. Logging in again worked. That is so "a la Windows" that i didn't even try. =) Thanks man

---

### Post by raul_ on 2006-09-17
Hey just one more thing. Everything works perfectly in the terminal, but when i edit for example, the firefox icon, and in the "command" field i type "firefox" it doesn't recognize the command...why is this?

---

### Post by crokett on 2006-09-17
Same reason it wouldn't work in Windows.  The icon doesn't know where the firefox executable is located.  You would need to put /firefox/firefox in the command field.  In Windows you also need the fully qualified path name unless you have the directory the file is in in your %PATH% system variable.

---

### Post by Najand on 2006-09-17
Make a symbolic link in /usr/bin; i.e.
```

sudo ln -s /firfox/firefox /usr/bin/firefox

```
It will work like the original firefox then.

---

### Post by raul_ on 2006-09-18
Oh ok...i just thought that in the UNIX OS, when an icon is launched, it creates some sort of "virtual shell" where it runs the command typed in the field "command". But apparently, the "command" field really reads "path" field right? :rolleyes:

---

