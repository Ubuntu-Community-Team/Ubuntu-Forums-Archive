---
title: "WINE problem, probably easier than I think..."
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by pHreaksYcle on 2008-02-11
So I am using WINE, it opens the programs installer easily. The app is called Tow Magic from Beacon Software. I really need this to work, it's honestly the only thing keeping my fathers business from switching over right now. Anyway, here's the issue. When it's done downloading the files from the internet, it says it failed at extracting them. So, I looked in the program files folder on the virtual C drive, nothing. No Tow Magic folder for me to manually extract the stuff and I find nothing of the sort on the whole virtual C drive. (I HAVE checked the show hidden files button just in case) Perhaps I am not looking in the right place, someone please have the answer lol. Any ideas would be appreciated, thank you!

---

### Post by oskar2000 on 2008-02-11
~./.wine/drive_c
Is that what you're looking for?

---

### Post by pHreaksYcle on 2008-02-11
Nah, man that's what I already looked in. Nothing. Thanks for quick response though.

---

### Post by kostkon on 2008-02-11
> **pHreaksYcle said:**
> Anyway, here's the issue. When it's done downloading the files from the internet, it says it failed at extracting them.

Hmmm. It says that it fails to extract the files not save them. Maybe the program downloads some form of compressed files, and then tries to call a specific external program to extract them. Do you know how actually the program works.

You could check the system requirements for the program to get a clue if anything else must be present in  the system in order this application to work as supposed.

---

### Post by pHreaksYcle on 2008-02-11
It did say some thing on the installer start page like it needed C++ something or other. Are these dependencies and how do I resolve those?

Thanks for your response.

---

### Post by oskar2000 on 2008-02-12
If you know what the filenames are, do a tracker search.
Or, from the command line:

```
find ~./.wine/ -name [filename]
```


In any case, if you are a paying customer, I would contact customer support, and - even though there is only a really small chance that they can help you, - the more people are interested in running this on linux, the more likely they will start supporting it.

---

### Post by oskar2000 on 2008-02-12
> **pHreaksYcle said:**
> It did say some thing on the installer start page like it needed C++ something or other. Are these dependencies and how do I resolve those?

Thanks for your response.

search for the exact line of the wine command, chances are that there are a couple of programs that have the same requirement. You should find a solution if there is one.

---

### Post by pHreaksYcle on 2008-02-12
Excuse me for my ignorance, but what WINE command are you referring to? I wasn't using the CLI, probably should though now that I think about it. I've actually gotten into contact with the owner of the company and he said he could make another version without compression. I am going to ask him to give that a try and see what happens.

---

### Post by oskar2000 on 2008-02-12
My brain seemed to have had an error there. 
Of course I meant to say: "... the exact line of the error" - which tells you that you are missing c++ - something.

Just in case you need it though:

If you open the program through a desktop icon, you can right-click it and go to the "launcher" tab to look up what the command is that this launcher executes. If it's in the program menu, the I don't know... you'll have to navigate into the program folder:

~/.wine/drive_c/Program Files/.../

and look for the right executable (*.exe) and start it with "wine [executable]".

---

