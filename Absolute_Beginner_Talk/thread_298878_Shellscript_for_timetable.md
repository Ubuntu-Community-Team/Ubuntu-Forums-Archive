---
title: "Shellscript for timetable"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by Bagboy23 on 2006-11-13
I have a time table which is in a table like this and stored in a file:

N O V E M B E R
Day Morning Noon Evening Night
01  MTS     TSN  MTS     RMT
02  CRD     ITW  ONF     IUE
03  AQW     FDE  NJY     NKU
...

Now this time table is really long, almost 12000 lines, so what i want it to do is identify the current date: day and month then just print out that line. For example, if today was the 3rd November it would print the lines:

N O V E M B E R
Day Morning Noon Evening Night
03  AQW     FDE  NJY     NKU

I have so far managed to work out:

myDate="$(date +%B)"
myDate2="$(date +%d)"
echo $myDate
grep $myDate & $myDate2

Probably all wrong. Can someone suggest something?

---

### Post by po0f on 2006-11-13
Bagboy23,

Do the month lines have spaces in them in the file?

---

### Post by Bagboy23 on 2006-11-13
Yes, or I can remove the spaces.

---

### Post by weresheep on 2006-11-13
Hi,

I've written a script which I think will do what you want. I have assumed though that there is only one e.g. "N O V E M B E R" in the file. You'll need to edit the script and change the line "FILE=info.txt" to whatever and whereever your time table file is. You may also need to add executable permissions to the file with the command 

chmod +x timetable.sh

Let me know if it works. Feel free to ask questions if something doesn't make sense.

There are many ways to solve a problem (especially on a *nix system) and mine almost certainly isn't optimal but over time as you learn more about using the command line tools you can improve the script. I am constantly going back and rewriting my scripts as I learn new tools / commands.Oh yeah, use this script at your own risk cos if it kills your system I don't want you blaming me :-D 

-weresheep

---

### Post by weresheep on 2006-11-14
I think you may need to fix something in my script. Near the bottom of the script there is a line with "grep -A 31" in it. This needs to change to "grep -A 32". The reason for this is because I forgot to take into account the column header line that appears after the month line.

Hope that makes sense.

-weresheep

---

### Post by Bagboy23 on 2006-11-14
Weresheep, thanks so much. It worked perfectly and I am using it for other things too. 

Also, I developed a script which installs ATI and BERYL in one go, without modification, maybe I could give it to you to develop further and sort out the kinks? Please let me know, I know a lot of ATI people would love this.

Thanks again for your help.:-D

---

### Post by Arndt on 2006-11-14
> **Bagboy23 said:**
> I have a time table which is in a table like this and stored in a file:

N O V E M B E R
Day Morning Noon Evening Night
01  MTS     TSN  MTS     RMT
02  CRD     ITW  ONF     IUE
03  AQW     FDE  NJY     NKU
...

Now this time table is really long, almost 12000 lines, so what i want it to do is identify the current date: day and month then just print out that line. For example, if today was the 3rd November it would print the lines:

N O V E M B E R
Day Morning Noon Evening Night
03  AQW     FDE  NJY     NKU

I have so far managed to work out:

myDate="$(date +%B)"
myDate2="$(date +%d)"
echo $myDate
grep $myDate & $myDate2

Probably all wrong. Can someone suggest something?

I haven't looked at the suggested shell script, which is probably perfectly fine, but here is a 'sed' one-liner that seems to do what you want:

```
$ sed -n "/N O V/,\${1,2p;/^03/p}" </tmp/calendar
```

If you keep the month and day in the variables MONTH and DAY, you can do

```
$ sed -n "/$MONTH/,\${1,2p;/^DAY/p}" </tmp/calendar
```

---

### Post by weresheep on 2006-11-14
Hi Arndt,

I had a look at your one liner, nice and neat. I noticed though, that it also finds other matching days from subsequent months. For example using today (November 14th) with the below data...


N O V E M B E R
Day Morning Noon Evening Night
01 aaaa
02 aaaa
...
14 aaaa
15 aaaa

D E C E M B E R
Day Morning Noon Evening Night
01 bbbb
02 bbbb
...
14 bbbb
15 bbbb


Your command prints...

N O V E M B E R
Day Morning Noon Evening Night
14 aaaa
14 bbbb

Do you know of a way to limit sed to one match? I've only used sed in basic ways and don't fully understand your command. At least not yet :-D

This may or may not be the behaviour the original poster wants, but I am interested for myself as it took me a while to think of a way to get only one match for the 'day' in my script.

Thanks.

-weresheep

---

### Post by weresheep on 2006-11-14
Hi Bagboy23,

I am glad my script worked ok, it was quite fun getting it working.

I've not used or installed the ATI drivers or BERYL before (I don't think my computer is up to running any of the modern 3D desktop stuff) so I don't know how much help I can be. But I can certainly take a look at what you have and see if I can come up with any improvements.

-weresheep

---

### Post by Arndt on 2006-11-14
> **weresheep said:**
> Hi Arndt,

I had a look at your one liner, nice and neat. I noticed though, that it also finds other matching days from subsequent months. For example using today (November 14th) with the below data...


N O V E M B E R
Day Morning Noon Evening Night
01 aaaa
02 aaaa
...
14 aaaa
15 aaaa

D E C E M B E R
Day Morning Noon Evening Night
01 bbbb
02 bbbb
...
14 bbbb
15 bbbb


Your command prints...

N O V E M B E R
Day Morning Noon Evening Night
14 aaaa
14 bbbb

Do you know of a way to limit sed to one match? I've only used sed in basic ways and don't fully understand your command. At least not yet :-D

This may or may not be the behaviour the original poster wants, but I am interested for myself as it took me a while to think of a way to get only one match for the 'day' in my script.

Thanks.

-weresheep

'sed' has a "quit" command named 'q', so this command is better:

```
$ sed -n "/N O V/,\${1,2p;/^03/{p;q}}" </tmp/calendar
```

But there is another flaw. If for some reason the specified date doesn't appear in the chosen month, my command will print the next one it finds, in any month. Instead of looking at everything below the specified month name, we can look at only the piece up to the next month:

```
$ sed -n "/N O V/,/[A-Z] /{1,2p;/^03/{p;q}}" </tmp/calendar
```

It's always a good idea to write some comments around a command line like this, if it's not a one-shot command, since it depends heavily on the format of the input. Or write it in something more readable to begin with, if it's likely to be extended or updated.

---

### Post by weresheep on 2006-11-14
Hi Arndt,

Thanks for expanding your original solution and for your explanation. I think I will need to play around with sed some more using the syntax you used to really get the hang of it. Thanks for the help.

:) 

-weresheep

---

### Post by Bagboy23 on 2006-12-01
For some reason, this script stopped working today (1st December), anyone know what's up with it?

---

### Post by weresheep on 2006-12-13
Hi,

I replied to your private message with an updated script as I didn't notice that you'd posted to this thread. Have you had any luck getting it to work?

-weresheep

---

