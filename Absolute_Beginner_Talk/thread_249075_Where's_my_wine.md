---
title: "Where's my wine?"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-09-02
Hi all!

I have installed a few things with wine, but I can't find them in the Applications list.  The only one I can find is one that has a desktop icon.  There is no mention of wine or of the installed programs.

Russty.

---

### Post by croak77 on 2006-09-02
Did they install in your wine folder? You can run it from a terminal with wine ~/.wine/drice_c/Program\ Files/xxx/program.exe or wherever your fake windows folder is.

---

### Post by Russty of Oz on 2006-09-02
> **croak77 said:**
> Did they install in your wine folder? You can run it from a terminal with wine ~/.wine/drice_c/Program\ Files/xxx/program.exe or wherever your fake windows folder is.

Im not sure what all that means?  Is there a way I can just find what is in the wine folder and click it?

---

### Post by bodhi.zazen on 2006-09-02
> **Russty of Oz said:**
> Hi all!

I have installed a few things with wine, but I can't find them in the Applications list.  The only one I can find is one that has a desktop icon.  There is no mention of wine or of the installed programs.

Russty.

I presume you are talking about your applications menu.

In general, wine programs do not insert themselves into your gnome/kde menu.

In explanation of the previous post:
~ = /home/username.

Your wine folder is a dot file (ie .wine) in your home directory and is thus hidden.
The path is /home/user_name/.wine

to start a wine program, in general, in a terminal type:
wine /full_path_to_exe_file

ie
```
wine /home/user_name/.wine/fake_c_drive/Program\ Files/Program/program.exe
```

To make life easier you can add launchers in gnome or desktop icons.

---

### Post by bodhi.zazen on 2006-09-02
> **Russty of Oz said:**
> Im not sure what all that means?  Is there a way I can just find what is in the wine folder and click it?

In your file browser options -> show hidden files will show your wine folder.

It will be listed as .wine, however.

---

### Post by Russty of Oz on 2006-09-02
OH!  I think I see, I will give it a try.  I just have to work out exactly what things are called. 

Thanks.
 
Russty.

---

### Post by Russty of Oz on 2006-09-02
> **bodhi.zazen said:**
> In your file browser options -> show hidden files will show your wine folder.

It will be listed as .wine, however.

Where is the "file browser opitons"?  I can't see them.

---

### Post by Russty of Oz on 2006-09-02
IT'S OK NOW!!

I just started the KDE task bar thing and in the Applications list, there is a wine folder!  It wasn't there before, so I don't know what has happened.  Perhaps it was one of those codes above I tried that showed it.

Thanks!

Russty:)

---

