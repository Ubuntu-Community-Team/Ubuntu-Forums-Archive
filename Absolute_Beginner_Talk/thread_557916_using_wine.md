---
title: "using wine"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by H_91 on 2007-09-23
Hi =]

How do you get WINE to actually work? I got through the settings by using this code
```
wineconfig
```

Other than that,..... ?
I have no idea what to do..

---

### Post by Dr Small on 2007-09-23
```
wine /path/to/program/filename.exe
```

---

### Post by runemaste644 on 2007-09-23
Or rather you can open a window in Nautilus, right click the application and select open with wine

Personally i like to use the CLI but i do not for that

---

### Post by H_91 on 2007-09-23
> **Dr Small said:**
> ```
wine /path/to/program/filename.exe
```

typed the right location and name of the setup, but it says that it cannot be found..

can you please show me an example just to make sure?

---

### Post by oneadvent on 2007-09-23
It also has a lot to do with what you are trying to run. If it is a main stream program, you can find plenty of help online.

I can run everything except things with a high ODBC driver dependency, but I am getting closer at that also.

---

### Post by H_91 on 2007-09-23
> **runemaste644 said:**
> Or rather you can open a window in Nautilus, right click the application and select open with wine

tried that.. doesn't work.
nothing happens.

---

### Post by cogadh on 2007-09-23
Go to Wine's Application Database and look up the applications you are trying to run. It will tell you first if they can run and second what you might need to do to make them run:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

You might also want to click on the "Stuff I've learned about Wine" link in my sig. It will give you some general pointers on how to use Wine.

EDIT -  Don't use the right-click method to run applications with Wine, use the terminal instead. If you use the terminal, any errors produced by Wine that could be used for troubleshooting will be output to the terminal. Using the right-click method, you lose those error messages.

---

### Post by oneadvent on 2007-09-23
What are you trying to run?

Also, typing it in a terminal will give you why it is not working.

---

### Post by H_91 on 2007-09-23
> **cogadh said:**
> Go to Wine's Application Database and look up the applications you are trying to run. It will tell you first if they can run and second what you might need to do to make them run:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

You might also want to click on the "Stuff I've learned about Wine" link in my sig. It will give you some general pointers on how to use Wine.

EDIT -  Don't use the right-click method to run applications with Wine, use the terminal instead. If you use the terminal, any errors produced by Wine that could be used for troubleshooting will be output to the terminal. Using the right-click method, you lose those error messages.


Really cool guide, thank you!! =D

---

