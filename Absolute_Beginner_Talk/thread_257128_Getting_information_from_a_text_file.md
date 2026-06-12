---
title: "Getting information from a text file?"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-09-14
Ive installed lm-sensors with sensord daemon on my machine. It logs all data to a file called syslog...(var/log/syslog) Do you know if its possible to retrieve certain data from this text file(and text files in general)and write it to a linux equivilent of an excel sheet whatever that is?

---

### Post by Najand on 2006-09-14
I think they  are a lot of different ways.
I use this way. Think you have a text file
like text and it is seperated by "tab".
I do:
```

sudo cp text text.tsv

```
then you can open it using 
Gnumeric spreadsheet.

---

### Post by meniscus on 2006-09-14
So let me get this right!

This command...[COLOR="Red"]sudo cp text text.tsv[/COLOR]copies the the file text to destination text.tsv? Is that right?

---

### Post by meniscus on 2006-09-14
Where does text.tsv exist after that? In the same folder?

---

### Post by Najand on 2006-09-14
yeah... If you want to put it somewhere else like /path1/path2/path3/text.tsv use (for gnumeric), 
```

sudo cp text /path1/path2/path3/text.tsv  

```
I forgot to say... If you want to use OpenOffice use:
(for openoffice.org)
```

sudo cp text /path1/path2/path3/text.[COLOR="Red"]csv[/COLOR]

```

Run OpenOffice Calc and open text.csv. Calc will ask for
format of the file, in the Separated By section of the pop-up screen,
click on Tab and uncheck Comma.

---

### Post by meniscus on 2006-09-14
Is there any way to set something like this up... So the values from the text file(syslog)are periodically transfered to the new excel file without me have to type cp every time?

---

