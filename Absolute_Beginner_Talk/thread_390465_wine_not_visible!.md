---
title: "wine not visible!"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by hardikorama on 2007-03-22
I am having a weird problem with wine :( . though i installed it using synaptic, i m unable to see it in 'applications' and also not able to use it when i click 'open with'. i tried re-installing it, but it didn't work. and i also want to knw if there are any game emulators available for ubuntu. thanks.

---

### Post by Josh1 on 2007-03-22
If you have installed WINE, try typing in:

```
winecfg
```

A window should pop up with options. If it doesn't, try installing it from their site.

[http://winehq.com/site/download-deb](http://winehq.com/site/download-deb)

Also, to wine things type into the console

```
wine programname.exe
```

---

### Post by hardikorama on 2007-03-22
I tried the code 

                        ```
wine programname.exe
```

and got the following error

                                          ```
 wine: could not load L"c:\\windows\\system32\\programname.exe": Module not found
```


now while running ```
winecfg
``` the moment i click on 'Audio', it crashes. i tried changing other options, but nothing worked.

---

### Post by Josh1 on 2007-03-22
Sorry for the confusion, winecfg stands for "WINE Configuration". You can change options, but defaults should be fine! :)

To WINE a Windows application, simply type in:

```
wine programname.exe
```

For example, to wine a program called office, i would type in:
```
wine office.exe
```

You will need to be in the same directory as the exe program, so for example put an exe program into your home directory then type:
```
cd ~
wine myprogram.exe
```

cd ~ means change to the home directory.

Goodluck :)

---

### Post by hardikorama on 2007-03-22
this, though being an effective method, seems a bit tedious. earlier, i only had to double click an 'exe' file to run it. also, i need to copy the entire folder of any program that i have to run. just wanted to know if u can provide me with a code for completely removing and re-installing wine. thanks for your help.

---

### Post by jordanmthomas on 2007-03-22
Right click on an exe and go to properties.
On the "Open With" tab, click 'Add'
On the window that comes up, Click the 'Use a custom cammand' field.
In this box, just type wine
Click Add, then close the window and you should be set

---

### Post by hardikorama on 2007-03-22
thanks! it worked.

---

