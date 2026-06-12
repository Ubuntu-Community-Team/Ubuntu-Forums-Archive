---
title: "Automatic Wine Launch"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by amrclutch1 on 2007-07-16
When I double click an file with an "exe" extension it fails of course. Is it possible to make it so when I double click it the program calls a script that has variables pertaining to the exe's name and the path to the file with the word "wine" in front of it, something like this... I don't know how to script well, so don't make fun of me lol.

```

if(filetype == (msi))
       msiexec ${PATH}/${FILENAME}
else if(filetype == (exe))
       wine ${PATH}/${FILENAME}

```

Of course this is just concept, I know that these functions aren't in the correct syntax, would it be possible to do this?

---

### Post by Al3xK3aton on 2007-07-16
Are you sure you have Wine installed? It won't work if you don't have it.

---

### Post by amrclutch1 on 2007-07-16
What I mean is if you double click it. Yes I have it installed I have steam and CSS installed. You should re-read my post.

---

### Post by Majorix on 2007-07-16
Follow this:
1. Right click an exe file.
2. Click Properties.
3. Go to the Open With tab.
4. There click Add.
5. Custom command.
6. Type in "wine" without the quotes.

Now anytime you try to open an exe file, it will be loaded using wine.

---

### Post by amrclutch1 on 2007-07-16
Wow, thanks man, never even thought it would be that simple. ;)

Just tried it and it says Cannot open Setup.exe, it is implying that it is a security risk, which I guess it is since it would make it just like windows. I never thought of that, thanks for the help though, I changed my mind :/

---

