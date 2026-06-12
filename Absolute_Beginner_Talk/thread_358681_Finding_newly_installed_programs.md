---
title: "Finding newly installed programs"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by macruadhi on 2007-02-11
I just installed a program called "Danger from the deep" and now I can't find it at all. I've use the "searth for files" command and it still doesn't find it. I'm not familiar enought with the linux file system yet to find it the tried and true way.

Thanks

---

### Post by RomeReactor on 2007-02-11
The program name for Danger From The Deep is actually **dangerdeep**; try running it from the terminal. If you want to make a launcher, post back and we'll explain how.

---

### Post by macruadhi on 2007-02-11
eric@eric-laptop:~$ dangerdeep
Caught exception: Error opening directory '/usr/share/games/dangerdeep/objects/airplanes/'
Stack trace: (5 frames)
0x806ced3 in dangerdeep at ??:0
0x806b4b4 in dangerdeep at ??:0
0x806b58e in dangerdeep at ??:
0xb79f0ea2 in __libc_start_main at ??:0
0x804e291 in __gxx_personality_v0 at ??:0


And this is what happens when I run dangerdeep, hummmm.
thanks anyway

---

### Post by RomeReactor on 2007-02-11
This is from the [Danger From The Deep]("http://www.dangerdeep.net/download.php") site:

> From version 0.2.0 on you will need to download the binary or source package and the [data package]("http://prdownloads.sourceforge.net/dangerdeep/dangerdeep-data-0.2.0.zip?download") as well.

Did you install the game files on your home folder? if they *are* in "/usr/share/games/dangerdeep", try

```
sudo chmod 777 -R /usr/share/games/dangerdeep
```

and run dangerdeep again.

---

### Post by macruadhi on 2007-02-12
Yup I got it. Now how do I install it?

---

### Post by RomeReactor on 2007-02-12
Open a Terminal (Applications-->Accessories-->Terminal), then write

```
sudo nautilus
```

This will open your file browser in "Administrator mode", so you can copy, create or erase files and folders even outside your home directory. **Be careful not to erase any file outside your home directory while Nautilus is opened  this way**. When Nautilus opens, go to where you downloaded the .zip data file and extract it. It will extract a directory called **data**. Now enter that directory and copy everything inside it (press **CTRL+A**, then **CTRL+C**); Still in Nautilus, go to **/usr/share/games** and create a directory called **dangerdeep** (right-click and select the first option, "Create Folder"). Go inside the newly created directory and paste the files (Press **CTRL+V**).

Now run **dangerdeep**.

---

### Post by macruadhi on 2007-02-12
Thank you, I'm still used to Windows .exe files and expecting everything to be installed at once. 
But it worked and I think you very much.

Eric

---

