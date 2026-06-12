---
title: "curl display"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-02-07
Is there a way I can change the way it displays the progress when it downloads?  It gives out a line for each second.  And I find that highly unnecessary.  Is there a way I can change progress output so the display would be like a bar just like in wget?  Or at least just the progress percentage.

---

### Post by Kapre on 2006-02-07
[QUOTE=tux101]Is there a way I can change the way it displays the progress when it downloads?  It gives out a line for each second.  And I find that highly unnecessary.  Is there a way I can change progress output so the display would be like a bar just like in wget?  Or at least just the progress percentage.[/QUOTE]

tux101 - are u using Gnome or KDE? Are we talking about the terminal screen or the synaptic screen downloading?

K

---

### Post by tux101 on 2006-02-07
Terminal screen.  It should not matter if it is KDE or GNOME.  Terminal behaves the same way for both.

---

### Post by cwaldbieser on 2006-02-07
[QUOTE=tux101]Is there a way I can change the way it displays the progress when it downloads?  It gives out a line for each second.  And I find that highly unnecessary.  Is there a way I can change progress output so the display would be like a bar just like in wget?  Or at least just the progress percentage.[/QUOTE]
What command line/options are you currently using.  -s/--silent should turn off any output.  -#/--progress-bar shows a progress bar.

---

### Post by tux101 on 2006-02-07
Thanks for the reply.  But it didn't make a big difference with the -#.  All it did was replace the statistics it was showing before with lines of #s.  It is still outputting a new line every second.  Is there a way I can keep it one line and still see the progress?

Like in wget, all you will see is something like this:

[===============>_______________] 50% 3.25K/S

Or something like that.

---

### Post by cwaldbieser on 2006-02-07
[QUOTE=tux101]Thanks for the reply.  But it didn't make a big difference with the -#.  All it did was replace the statistics it was showing before with lines of #s.  It is still outputting a new line every second.  Is there a way I can keep it one line and still see the progress?

Like in wget, all you will see is something like this:

[===============>_______________] 50% 3.25K/S

Or something like that.[/QUOTE]
Can you explain how exactly you are using it?  I am using it from a KDE konsole to download a knoppix ISO right now, and the statistics displayed update on a single line (curses library?).  Are you piping or redirecting the stdout/stderr of the command?

My command line is:
```

$ curl -o KNOPPIX_V4.0.2CD-2005-09-23-EN.iso ftp://ftp.uni-kl.de/pub/linux/knoppix/KNOPPIX_V4.0.2CD-2005-09-23-EN.iso

```

---

### Post by tux101 on 2006-02-09
Messed up icons.  Thought pencil on paper was edit.  Ended up replying a new message.

See below.

---

### Post by tux101 on 2006-02-09
```

curl -O http://www.babytux.org/gallery/images/tuXper-alt.jpg
  % Total    % Received % Xferd  Average Speed   Time    Time
  Time  Current
                                 Dload  Upload   Total   Spent  
  Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:12 
  2 86804    2  2582    0     0    179      0  0:08:04  0:00:14 
  4 86804    4  4022    0     0    266      0  0:05:26  0:00:15 
  9 86804    9  8342    0     0    515      0  0:02:48  0:00:16
 11 86804   11  9782    0     0    576      0  0:02:30  0:00:16 
 12 86804   12 11222    0     0    624      0  0:02:19  0:00:17
 26 86804   26 22742    0     0   1192      0  0:01:12  0:00:19
 44 86804   44 38582    0     0   1931      0  0:00:44  0:00:19 
 79 86804   79 68822    0     0   3278      0  0:00:26  0:00:20
100 86804  100 86804    0     0   4066      0  0:00:21  0:00:21 
--:--:-- 17540

```

---

### Post by cwaldbieser on 2006-02-09
[QUOTE=tux101]```

curl -O http://www.babytux.org/gallery/images/tuXper-alt.jpg
  % Total    % Received % Xferd  Average Speed   Time    Time
  Time  Current
                                 Dload  Upload   Total   Spent  
  Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:12 
  2 86804    2  2582    0     0    179      0  0:08:04  0:00:14 
  4 86804    4  4022    0     0    266      0  0:05:26  0:00:15 
  9 86804    9  8342    0     0    515      0  0:02:48  0:00:16
 11 86804   11  9782    0     0    576      0  0:02:30  0:00:16 
 12 86804   12 11222    0     0    624      0  0:02:19  0:00:17
 26 86804   26 22742    0     0   1192      0  0:01:12  0:00:19
 44 86804   44 38582    0     0   1931      0  0:00:44  0:00:19 
 79 86804   79 68822    0     0   3278      0  0:00:26  0:00:20
100 86804  100 86804    0     0   4066      0  0:00:21  0:00:21 
--:--:-- 17540

```[/QUOTE]

Strange.  When I do the same command, It just overwrites the current line.

Here is the version I am using.
```

$ type curl
curl is /usr/bin/curl
$ curl --version
curl 7.14.0 (i486-pc-linux-gnu) libcurl/7.14.0 OpenSSL/0.9.7g zlib/1.2.3 libidn/0.5.13
Protocols: ftp gopher telnet dict ldap http file https ftps 
Features: IDN IPv6 Largefile NTLM SSL libz 

```
Also, I tried it on both a KDE konsole and gnome-terminal.

---

