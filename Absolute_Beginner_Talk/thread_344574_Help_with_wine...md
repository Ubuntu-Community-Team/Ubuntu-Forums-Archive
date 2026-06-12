---
title: "Help with wine.."
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by I_have_seen_the_light on 2007-01-23
I am running xubuntu Dapper. I just installed wine and was looking for a launcher that I cold click so that i could configure it.  (I was hoping for the same dialog boxes of wine that I saw when I used Knoppix)  after donwloading wine, I was not able to see a launcher so I went to the terminal to launch it from there. but no boxes showed up.  :( 

Is there a way so that I could configure/set up wine within a GUI? or at least from menu?

thanks!

---

### Post by JamieC on 2007-01-23
To configure wine, open a terminal window and type the following:
```

winecfg

```

To launch applications within wine use the following (where <file> is the path to the executable):
```

wine "<file>"

```

---

### Post by I_have_seen_the_light on 2007-01-23
thanks!  but unfortunately, I am still confused.  can you point me to a tutorial onhow to use wine?

Thanks,

---

### Post by PriceChild on 2007-01-23
[uwiki]Wine[/uwiki]

---

### Post by Jussi01 on 2007-01-23
So, what the man said is, 

Go to terminal. (applications -> accessories -> terminal)

Then type 

```
winecfg
``` 

and press enter, this will bring up a gui for wine. (it looks similar to a windows config box).

Then, once you have done that, and put in what ever settings you like, then you can do one of 2 things. 

*Right click on the .exe file you want to run and click "run with wine" (or something similar)*

**or**

*Go to terminal and type:*

```
wine <the path of the file here>
```

So, for example:

```
wine /home/jussi01/utorrent.exe
```


Hope this helps

---

