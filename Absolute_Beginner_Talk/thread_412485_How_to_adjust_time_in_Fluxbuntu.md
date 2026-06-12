---
title: "How to adjust time in Fluxbuntu?"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by akl604 on 2007-04-18
I am an absolute beginner trying to figure out how Linux works and I have been advised [here]("http://ubuntuforums.org/showthread.php?t=404243&page=2") to install Fluxbuntu. Hopefully here is also the correct place to ask this question.

So I have installed Fluxbuntu successfully. After some Googling, I have also managed to edit the clock format to my liking (which is great).  However, the time shown is 12 hours ahead of my current time here in New Zealand. How do I adjust it?

---

### Post by Renegade of Funk on 2007-04-18
You need to set the timezone properly:
- Open an terminal window
- Type: cp /usr/share/zoneinfo/<CONTINENT>/<CITY> /etc/timezone 

After that your time micht still not be right. This can be changed by the date application.
Type in the console: date --help
for the complete syntax but you will need: date MMDDhhmm

Cheers

---

### Post by akl604 on 2007-04-18
Thanks. I remember having setup the time zone correctly when I was installing Fluxbuntu. But, as you suggested:

> - Type: cp /usr/share/zoneinfo/<CONTINENT>/<CITY> /etc/timezone

I typed:

```
cp /usr/share/zoneinfo/oceania/auckland/etc/timezone
```

but it replied to me

```
cp: missing destination file operand after 'cp /usr/share/zoneinfo/oceania/auckland/etc/timezone'
```

Huh?

I also tried your advice

> Type in the console: date --help
for the complete syntax but you will need: date MMDDhhmm

but it mainly showed me how to format the time (which I had already managed to do in the past - I have **Thu 19 Apr 19:25**. I could not figure out how to set the time, though.

Sorry for the basic questions; as I said, I am an absolute beginner with Linux!

---

### Post by yabbadabbadont on 2007-04-18
```
sudo -s -H
echo "oceania/auckland" > /etc/timezone
cp /usr/share/zoneinfo/oceania/auckland /etc/localtime
date <put in the correct date and time in the format listed above>

```
/etc/timezone is just a text file that contains your timezone.  For example, mine has "US/Central".  /etc/localtime is either a copy of, or a symbolic link to, your timezone file in /usr/share/zoneinfo.

---

### Post by akl604 on 2007-04-18
Thanks for your patience. I think I typed the code correctly as you suggested, but at 

```
cp /usr/share/zoneinfo/oceania/auckland /etc/localtime
```

it replied to me

```
cp: cannot stat 'cp /usr/share/zoneinfo/oceania/auckland /etc/localtime' : No such file or directory
```

:|

---

### Post by yabbadabbadont on 2007-04-18
I just had a quick look in the /usr/share/zoneinfo directory, there isn't any "oceania" there.  ;)

Use /usr/share/zoneinfo/Pacific/Auckland instead.  :D

---

### Post by akl604 on 2007-04-18
Thanks; I am 2 steps closer:

1) For some reason, after a restart (and before even reading your latest message), my time is no longer 12 hours ahead... but 7 minutes late! So I am much closer, but I don't know why; and I still don't know how to adjust the time.

2) You are correct; Ubuntu / Fluxbuntu seem to think that Auckland is in a continent called "Pacific". So I am one step away from being able to adjust the time, **but** when I type

```
/usr/share/zoneinfo/Pacific/Auckland /etc/localtime
```

it says

```
-bash: /usr/share/zoneinfo/Pacific/Auckland /etc/localtime: Permission denied
```

If I type

```
cp /usr/share/zoneinfo/Pacific/Auckland /etc/localtime 
```


it says

```
cp: '/usr/share/zoneinfo/Pacific/Auckland' and '/etc/localtime' are the same file
```

If I type

```
date --set=04191117
```

or

```
date --set=AP191117
```

it says

```
date: invalid date
```

8-[

---

### Post by chalex on 2007-04-18
In general, you do not want to bother setting the date manually.  Your clock may drift and you'll have to do it again later.  Get the computer to do it for you via Network Time Protocol.  ```
apt-get install ntp
``` will do the right thing on Debian Etch, and won't require any further configuration.  Let me try it on my Ubuntu box...

EDIT: It will do the right thing on Feisty (since Feisty packages were synced with Etch ~6mo ago).  On 6.10 you may need to make some "server" entries in /etc/ntp.conf  Check the status of the time servers you're using with the command "ntpq -p".

---

### Post by akl604 on 2007-04-18
Thanks for the suggestion. I suppose the latter requires an internet connection. I haven't gone that far with that Fluxbuntu laptop and I am not connected to my network yet.

---

### Post by akl604 on 2007-04-22
I have managed to adjust the time!

One of my friends emailed me a long explanation about how the time works on Linux (I understood about 1% of it) and mentioned that I should try to turn the laptop on, and press F2.

Indeed, as soon as I did it, a screen appeared, and I could adjust the clock. See screenshot.
[IMG]http://yellow.markwolk.com/linuxtime.jpg[/IMG]
So I am left with only one question: why such a simple question generated so many different answers??? Is my case so unusual? :-k

---

### Post by yabbadabbadont on 2007-04-22
I think that we all assumed that you would have set the hardware clock to the correct time before messing about with timezones and such...  after all, changing the time in the BIOS has nothing to do with Windows or Linux or OS/2 or any operating system.  At least that was the assumption I made.  I guess it's true what they say about assuming things.  :D

---

### Post by akl604 on 2007-04-22
Many thanks for the explanation. I must admit I did not know that setting the clock was done without any operating system. As Molière's *Bourgeois Gentilhomme* did not know that he is speaking in prose. :)

---

