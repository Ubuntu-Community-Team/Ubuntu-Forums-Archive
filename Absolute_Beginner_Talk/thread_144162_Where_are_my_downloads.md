---
title: "Where are my downloads?"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by 2latesmart on 2006-03-13
Hi, 

I'm a complete newbie to linux but my Microsoft experience goes back to MSDOS.  I installed ubuntu and the news client pan.  All was going well as I flagged and downloaded some binary files.  My machine took the right amount of time to do the download but now I can't find the downloaded files.  pan is set to download to a default directory "home/username/News/pan" but I can't find the directory!  I tried using the file browser to drill down from "root" to "home" to "username" but there's no directory called "News" in "username".  There is a directory for "Desktop" in "username" but this also has no "News" directory.  A search for the name of the file downloaded was unsuccessful.

Where did my files go?

---

### Post by rfruth on 2006-03-13
home/username/ and /home are one in the same (if logged in as the same user) but hey I know what you mean, sometimes downloaded files seem to go in the bit bucket :mad: SO I created a folder named "download" and 1 called "images" & "file" in an effort to make life easier (I know where stuff ends up)  also I use the Desktop if all else fails :D

---

### Post by mustang on 2006-03-13
[QUOTE=2latesmart]Hi, 

I'm a complete newbie to linux but my Microsoft experience goes back to MSDOS.  I installed ubuntu and the news client pan.  All was going well as I flagged and downloaded some binary files.  My machine took the right amount of time to do the download but now I can't find the downloaded files.  pan is set to download to a default directory "home/username/News/pan" but I can't find the directory!  I tried using the file browser to drill down from "root" to "home" to "username" but there's no directory called "News" in "username".  There is a directory for "Desktop" in "username" but this also has no "News" directory.  A search for the name of the file downloaded was unsuccessful.

Where did my files go?[/QUOTE]

Are you logged into your root or user account? 

If it's the former, open nautilus

home->(username)->News->Pan

If it's the latter,

News->Pan

---

### Post by taurus on 2006-03-13
What happens if you run this command at the prompt.  Do you see all your downloads on the list?
```

ls -la ~/News/pan

```

---

### Post by 2latesmart on 2006-03-13
I tried creating a new directory but result was strange.  Downloaded file didn't appear in the new directory until I closed pan!

Here's the response to the command entered in terminal:

username@ubuntu:~$ ls -la ~/News/pan
total 12
drwx------        2 username username 8192 2006-03- 13 19:30 .
drwxr - xr - x   5 username username 4096 2006-03- 13 18:55 . .

Thanx for the replies

---

### Post by 2latesmart on 2006-03-13
Maybe I'm trying to solve the wrong problem. Let me rephrase my help request....

Which ubuntu compatible newsreader client is the best to download large (750M), many-part, binary files (videos in rar form with pars) from newsgroups such as alt.binaries.movies.divx.  I used Newsbin Pro on my Windows XP setup.

---

### Post by mustang on 2006-03-14
[QUOTE=2latesmart]Maybe I'm trying to solve the wrong problem. Let me rephrase my help request....

Which ubuntu compatible newsreader client is the best to download large (750M), many-part, binary files (videos in rar form with pars) from newsgroups such as alt.binaries.movies.divx.  I used Newsbin Pro on my Windows XP setup.[/QUOTE]

```
sudo apt-get install klibido
```

---

