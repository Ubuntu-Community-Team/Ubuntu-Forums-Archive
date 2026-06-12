---
title: "No search function? A shock"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by thecow on 2007-11-28
I was with some friends today, Windows users, and we were listening to music on my laptop.  I wanted to find something so I went to the handy "Search bar" in the file explorer.  To my utter surprise the search bar never found anything I searched for.  I eventually typed in things I knew existed and still nothing, I typed in the letter 'a' and nothing.  The Windows users found that hillarious, is there something I am missing here or is it impossible to search a portable hard drive?

---

### Post by master_kernel on 2007-11-28
Wow. I tried this too and it didn't work. Anyone know the answer? Maybe Beagle/Tracker is the way to go.

---

### Post by thecow on 2007-11-28
Ha Im using the command line to search.  If this isnt implemented correctly that's a HUGE oversight on the Ubuntu team's part

---

### Post by master_kernel on 2007-11-28
Yeah I use "locate something" from the command line to find stuff. Oh well, I'll go with Beagle.

---

### Post by Sef on 2007-11-28
Sounds like it wasn't working right.   I can search my usb key (a portable hard drive.)  Without the portable hard drive, can you search your onboard hard drive?  a usb key?

---

### Post by Majorix on 2007-11-28
I have the same problem since the first time I used Ubuntu. I search in the terminal instead:
```
sudo updatedb && locate *filename* > search_results.txt && gedit search_results.txt
```

Wait 3-4 minutes for the code to execute, and it will open a text editor with your search results in the end.

---

### Post by thecow on 2007-11-28
Well I know how to search from the terminal.  I just use ls | grep (insert here) to find a file.  
But its absurd to me that there is no usable graphical search function

I figure there must be something I am doing wrong honestly

---

### Post by master_kernel on 2007-11-28
> **Sef said:**
> Sounds like it wasn't working right.   I can search my usb key (a portable hard drive.)  Without the portable hard drive, can you search your onboard hard drive?  a usb key?
You can search it using Nautilus in 7.10?

---

### Post by Majorix on 2007-11-28
> **thecow said:**
> Well I know how to search from the terminal.  I just use ls | grep (insert here) to find a file.  
But its absurd to me that there is no usable graphical search function

I figure there must be something I am doing wrong honestly

ls lists only the files in the current directory. So unless you write a script that looks in all directories using that code, you aren't searching any folders except the working directory.

And to be honest, you aren't doing anything wrong, it's Ubuntu's (and Debian had it too) bug for a very long time.

---

### Post by jordanmthomas on 2007-11-28
It works for me (not using Ubuntu) but I figured I could still add something:
You can't use wildcards in nautilus's search.

*.mp3 returns nothing while .mp3 returns all my mp3s

---

### Post by Majorix on 2007-11-28
> **jordanmthomas said:**
> It works for me (not using Ubuntu) but I figured I could still add something:
You can't use wildcards in nautilus's search.

*.mp3 returns nothing while .mp3 returns all my mp3s

Odd thing I can use wildcards. Works by some, by some not. Told you, the Nautilus search function is as buggy as hell. Hope they fix it soon.

---

### Post by jordanmthomas on 2007-11-28
There's a way you can integrate beagle with nautilus so its search should work better (can't find it at the moment, though), and I believe there's a way to get Tracker in there too.

---

### Post by thecow on 2007-11-28
Yea ls works in directories.  Although if you search from directory '/' I think itll list everying it finds and you can have it list the directories the files are in.  

Anyways if anyone finds any way to get this operating system to perform one of its most basic tasks Id love to see the fix

---

### Post by jordanmthomas on 2007-11-28
> Yea ls works in directories. Although if you search from directory '/' I think itll list everying it finds and you can have it list the directories the files are in.
I think it'll only do that if you do 
```
ls -R / 
``` and I think it only goes 5 directories deep if I recall correctly.

To search, you should use find.
```
find . -iname query
```
will search through the current directory (up to 5 levels deep by default, but this is changeable)

You can use locate too, but it searches everywhere and you'd need to filter its results.

---

### Post by _sAm_ on 2007-11-28
> I was with some friends today, Windows users, and we were listening to music on my laptop. I wanted to find something so I went to the handy "Search bar" in the file explorer. To my utter surprise the search bar never found anything I searched for. I eventually typed in things I knew existed and still nothing,
 
If I go to Places(at top panel on desktop) > Search for files > There I change the «Look in Folder» to my external disk I can search for whatever I want. I agree, this should really be within the file manager Nautilus. 

Solution 2: Install Disksearch, see here; [http://www.getdeb.net/app.php?name=DiskSearch](http://www.getdeb.net/app.php?name=DiskSearch)

---

### Post by Billy_McBong on 2007-11-28
Tracker searches always give good results

---

### Post by thecow on 2007-11-28
Ah thankyou sam.  Yes that does work when I go to Places.  Odd that it doesnt work in the file manager though

---

### Post by _sAm_ on 2007-11-28
> **thecow said:**
> Ah thankyou sam.  Yes that does work when I go to Places.  Odd that it doesnt work in the file manager though

It will, its the same search engine. Go to Nautilus and press Ctrl + F and search for somthing. When you have done so press the + sign and change the location for the search to your external harddrive.

Tip; if you go to Nautilus and press "Help" > Contents > and choose "Searching For Files", you will get it explained:-)

---

### Post by master_kernel on 2007-11-28
This is very weird.

---

### Post by _sAm_ on 2007-11-28
> **master_kernel said:**
> This is very weird.

What is weird?

---

### Post by thecow on 2007-11-28
> **_sAm_ said:**
> It will, its the same search engine. Go to Nautilus and press Ctrl + F and search for somthing. When you have done so press the + sign and change the location for the search to your external harddrive.

Tip; if you go to Nautilus and press "Help" > Contents > and choose "Searching For Files", you will get it explained:-)

I am sorry my dear Sam.  But that does not work for me.

---

### Post by master_kernel on 2007-11-28
> **thecow said:**
> I am sorry my dear Sam.  But that does not work for me.
Nor for me.

---

### Post by _sAm_ on 2007-11-28
> **thecow said:**
> I am sorry my dear Sam.  But that does not work for me.

Take a look at the picture, here I have changed the search location to an external USB drive within Nautilus.

---

### Post by thecow on 2007-11-28
Ha, Sam, I do not know exactly how much of a retard you think I am.  But believe me, I am aware of what you are trying to explain to me, yet I still must inform you that the error is very real

---

### Post by _sAm_ on 2007-11-28
> **thecow said:**
> Ha, Sam, I do not know exactly how much of a retard you think I am.  But believe me, I am aware of what you are trying to explain to me, yet I still must inform you that the error is very real

Looks like I am the real "retard" here, cus I didn't understand you. Sorry about that. If there is a bug you could check over at Lunsphad(or what its called) and see if others have posted about it.

---

### Post by master_kernel on 2007-11-28
> **thecow said:**
> Ha, Sam, I do not know exactly how much of a retard you think I am.  But believe me, I am aware of what you are trying to explain to me, yet I still must inform you that the error is very real
:lol:

He's right; it's real. Here's proof in the attachment.

---

### Post by thecow on 2007-11-28
Don't fret brother

---

### Post by gaspard.leon on 2007-11-29
Sweet!!

It's not just me!

I thought i was just thick, missing some philosophical difference in searching using ubuntu vs windows...

My first attempts: Open a place in nautilus, click "Search" type something (if you like, choose something you know exists), press enter, nothing, you get blank search results, and the disk light does not flash to indicate something is happening...

I have (since reading this thread) tried the Places > Search for Files... option, that works as expected, it appears busy for a little while then comes up with some results...

... I was also trying the little "Deskbar Applet" but have been discouraged by that, it works mostly, but doesn't appear to search my ntfs drives... which I can live with now that I know to use Places > Search for Files... 

It just seems strange that nautilus' search function appears to be "braindead" as in I don't understand it... I assume it's using some other type of criteria for the search, like in file contents or some such...

anyways, meh, i have a feasible solution for now...

And I've changed my indexing preferences today to include my ntfs drives for tracker, and we'll see if that helps down the road once it's indexed those drives.
[B]
One more thing: Anyone know how to change the behaviour of the button in nautilus, I would like it to open that Search for Files... dialog, since that works so well...
[/B]
cheers,

Gaspard

---

