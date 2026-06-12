---
title: "View as thumbnail"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by rizzyc on 2005-12-31
I managed to make my Ubuntu Linux look nice and stuff and i really love it over xp now, but the problem is that when i have to open an image file i dont know what it looks like because there is no view as thumnail option in the standard open comman d of any program... 

For example I am trying to add emoticons to Amsn and i dont knwo what im adding cuz i need to see it.. thas one thign good about xp but i'm sure there is a way to do it in Ubuntu too..

another thing is that my add Applications button disappeared... i dont know how that happened?

---

### Post by Sutekh on 2005-12-31
[QUOTE=rizzyc]I managed to make my Ubuntu Linux look nice and stuff and i really love it over xp now, but the problem is that when i have to open an image file i dont know what it looks like because there is no view as thumnail option in the standard open comman d of any program... 

For example I am trying to add emoticons to Amsn and i dont knwo what im adding cuz i need to see it.. thas one thign good about xp but i'm sure there is a way to do it in Ubuntu too..
[/QUOTE]
The only thing I can think of is to have a browser open to the folder at the same time as when you are choosing the file.

[QUOTE=rizzyc]
another thing is that my add Applications button disappeared... i dont know how that happened?[/QUOTE]

Go to the Menu Editor; Applications -> System Tools -> Application Menu Editor
and see if there is an entry under 'Applications' for the 'Add Applications' Program, it might be greyed/unchecked.

If it's not there at all, you can add it by clicking the 'New Entry' button and entering these details;
```

Name : Add Applications 
Comment : Install and remove applications 
Command : /usr/bin/gksudo /usr/bin/gnome-app-install

```
The command line is important, the others are up to you, but that's what my entry has.

The icon that I have is /usr/share/pixmaps/update-notifier.png

---

