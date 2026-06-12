---
title: "[SOLVED] check for spyware"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by jpeulen on 2008-02-08
How can I check for Spyware? In Google I get this response:

[B]Google 	
 Error 	 [/B]

  [B]  We're sorry...

    ... but your query looks similar to automated requests from a computer virus or spyware application. To protect our users, we can't process your request right now.

    We'll restore your access as quickly as possible, so try again soon. In the meantime, if you suspect that your computer or network has been infected, you might want to run a virus checker or spyware remover to make sure that your systems are free of viruses and other spurious software.

    If you're continually receiving this error, you may be able to resolve the problem by deleting your Google cookie and revisiting Google. For browser-specific instructions, please consult your browser's online support center.

    We apologize for the inconvenience, and hope we'll see you again on Google. 
[/B]
I also looked for virusses with AVG for Linux, (because the ClamAV can not get the Update Signatures)

---

### Post by imT on 2008-02-08
:lolflag: in linux you don't have viruses, spyware and trojans. in linux you just gotta check if your firewall is working, that's it...as for your problem try again with another user maybe that will help, you must did something wrong, is not the os :)

---

### Post by randy78 on 2008-02-08
> **jpeulen said:**
> How can I check for Spyware? In Google I get this response:

[B]Google 	
 Error 	 [/B]

  [B]  We're sorry...

    ... but your query looks similar to automated requests from a computer virus or spyware application. To protect our users, we can't process your request right now.

    We'll restore your access as quickly as possible, so try again soon. In the meantime, if you suspect that your computer or network has been infected, you might want to run a virus checker or spyware remover to make sure that your systems are free of viruses and other spurious software.

    If you're continually receiving this error, you may be able to resolve the problem by deleting your Google cookie and revisiting Google. For browser-specific instructions, please consult your browser's online support center.

    We apologize for the inconvenience, and hope we'll see you again on Google. 
[/B]
I also looked for virusses with AVG for Linux, (because the ClamAV can not get the Update Signatures)

This has happened to me in the past as well...

Certain Firefox extensions like TrackMeNot will cause this error, so your best bet is to disable all extensions and then add them back one at a time to see if that's the problem.

When this happens, they ban your ip for a bit, but you could go to Scroogle.org and that will allow you to search Google while hiding your IP...

Hope this helps ;)

---

### Post by TheDilettante on 2008-02-08
What were you searching? I know certain searches will set off google (e.g. the third request for any of the google hacks from searchlores.org) depending on what kind of information is sought after.

---

### Post by zabien1970 on 2008-02-08
> **imT said:**
> :lolflag: in linux you don't have viruses, spyware and trojans. in linux you just gotta check if your firewall is working, that's it...as for your problem try again with another user maybe that will help, you must did something wrong, is not the os :)

I have to both agree with you and disagree at the same time.

 'in linux you don't have viruses, spyware and trojans'   I disagree here this is correct most of the time but with inexperience you could still get one, I just read a thread here where a user purposely ran a windows virus in ubuntu to see what would happen  [http://ubuntuforums.org/showthread.php?t=72598](http://ubuntuforums.org/showthread.php?t=72598)

' you must did something wrong, is not the os :)' This is where I agree, the user could of hit agree or accept on a download from an untrusted site, typed in his password, and infected himself unknowingly, remember this is a beginner's forum, although he could still have a setting in firestarter I dont think google would think its an automated request.

 To the OP:
  What were you doing, or googleing when this error popped up?

---

### Post by randy78 on 2008-02-08
> **zabien1970 said:**
> I have to both agree with you and disagree at the same time.

 'in linux you don't have viruses, spyware and trojans'   I disagree here this is correct most of the time but with inexperience you could still get one, I just read a thread here where a user purposely ran a windows virus in ubuntu to see what would happen  [http://ubuntuforums.org/showthread.php?t=72598](http://ubuntuforums.org/showthread.php?t=72598)

' you must did something wrong, is not the os :)' This is where I agree, the user could of hit agree or accept on a download from an untrusted site, typed in his password, and infected himself unknowingly, remember this is a beginner's forum, although he could still have a setting in firestarter I dont think google would think its an automated request.

 To the OP:
  What were you doing, or googleing when this error popped up?

The user was infected because he allowed Wine access to his WHOLE drive...

As far as Google throwing up flags at searches, it doesn't.

Google is neutral and does not filter searches based on keywords.

Think about it...

I don't mean to sound crude, but it's almost like a lot of ex/current Windows users WANT there to be viruses in Linux... Seriously... 

A quick search on Google for "Linux Trojans" will reveal that there is nothing really to worry about, but why go for facts when you can just make something up on your own?

Aysiu has made great points regarding this and you will need to search the forums for your answers.

---

### Post by HermanAB on 2008-02-08
To come back to the question of how to look for spyware: 
$ sudo tcpdump -A -s 256 -i eth0

Cheers,

Herman

---

### Post by hyper_ch on 2008-02-08
> **randy78 said:**
> Google is neutral and does not filter searches based on keywords.

That's wrong. Google does filter/censor in certain countries.

---

### Post by randy78 on 2008-02-08
> **hyper_ch said:**
> That's wrong. Google does filter/censor in certain countries.

Right, you are 100% correct.

However, my own experience leads me to believe that the OP is using some type of Privacy software such as TOR or a Firefox extension which obfuscates cookie/referrer data, especially since the error is in English.

---

### Post by TheDilettante on 2008-02-08
Ultimately, OP's doing something wrong - if neither extension/privacy shield nor virus, the remaining option is the search itself.  OP, you should either cool it a minute, or scroogle or change from the IP google blocked.

---

### Post by randy78 on 2008-02-08
> **TheDilettante said:**
> Ultimately, OP's doing something wrong - if neither extension/privacy shield nor virus, the remaining option is the search itself.  OP, you should either cool it a minute, or scroogle or change from the IP google blocked.

I stand corrected ;)

However, I personally have never replicated this error while using advanced search operators, but what you say makes sense.

If the OP has TrackMeNot enabled, or is using TOR to search, try disabling those, restarting Firefox and waiting 5 minutes.

Thanks for the info guys!:guitar:

---

### Post by TheDilettante on 2008-02-08
Rock on!

---

### Post by imT on 2008-02-08
> **zabien1970 said:**
> I have to both agree with you and disagree at the same time.

 'in linux you don't have viruses, spyware and trojans'   I disagree here this is correct most of the time but with inexperience you could still get one, I just read a thread here where a user purposely ran a windows virus in ubuntu to see what would happen  [http://ubuntuforums.org/showthread.php?t=72598](http://ubuntuforums.org/showthread.php?t=72598)

i stand correctly, even thou you get a virus in wine, ubuntu/linux isn't affected at all.

---

### Post by jpeulen on 2008-02-10
> **zabien1970 said:**
> I have to both agree with you and disagree at the same time.

 'in linux you don't have viruses, spyware and trojans'   I disagree here this is correct most of the time but with inexperience you could still get one, I just read a thread here where a user purposely ran a windows virus in ubuntu to see what would happen  [http://ubuntuforums.org/showthread.php?t=72598](http://ubuntuforums.org/showthread.php?t=72598)

' you must did something wrong, is not the os :)' This is where I agree, the user could of hit agree or accept on a download from an untrusted site, typed in his password, and infected himself unknowingly, remember this is a beginner's forum, although he could still have a setting in firestarter I dont think google would think its an automated request.

 To the OP:
  What were you doing, or googleing when this error popped up?

I was looking for used industrial fryers for making corn chips. That is actually the business I am in.

---

### Post by jpeulen on 2008-02-10
> **HermanAB said:**
> To come back to the question of how to look for spyware: 
$ sudo tcpdump -A -s 256 -i eth0

Cheers,

Herman

I used that command and it keeps on going and going with a lot of lines like  these: e.g.

[B]07:31:51.283681 IP 10.0.0.1.51331 > cpe-24-94-243-220.sw.res.rr.com.63829: . ack 144 win 13090
E..(..@.@.M.
....^.....U..n....BP.3"vH..
07:31:51.283881 IP 10.0.0.1.51331 > cpe-24-94-243-220.sw.res.rr.com.63829: P 592:596(4) ack 144 win 13090
E..,..@.@.M.
....^.....U..n....BP.3"}@..
...
07:31:51.774897 IP cpe-24-94-243-220.sw.res.rr.com.63829 > 10.0.0.1.51331: . ack 596 win 65125
E@.(.O@.q.L..^..
....U.....B..n.P..e..........
07:31:56.163701 IP 10.0.0.1.ntp > europium.canonical.com.ntp: NTPv4, Client, length 48
E..L..@.@.v.
...[.^..{.{.8A.#.....]V..       ..O...Y
f.._..Y
.Pck    .Y
......Y
.).Rx
[/B]

What does this mean? Do I have spyware or not? I only copied a few lines to show you. However the lines are all different.

This is what I got when I pressed "Ctrl C"

[B]900 packets captured
978 packets received by filter
67 packets dropped by kernel
[/B]

---

### Post by jpeulen on 2008-02-10
> **TheDilettante said:**
> Ultimately, OP's doing something wrong - if neither extension/privacy shield nor virus, the remaining option is the search itself.  OP, you should either cool it a minute, or scroogle or change from the IP google blocked.

I still can not get into "Google" it is now a few days. But the point is that there is something funny with my computer. How can I change the IP address? But that still does not make sure there is no spy ware. I do my banking from this machine.  

By the way what is "OP" standing for?? "Obvious (P)idioot? :redface:  :)

---

### Post by jpeulen on 2008-02-10
> **randy78 said:**
> I stand corrected ;)

However, I personally have never replicated this error while using advanced search operators, but what you say makes sense.

If the OP has TrackMeNot enabled, or is using TOR to search, try disabling those, restarting Firefox and waiting 5 minutes.

Thanks for the info guys!:guitar:

Where can disable or enable Trackmenot?? What is TOR?  :redface:  :confused:

---

### Post by spiderbatdad on 2008-02-10
```
sudo apt-get install rkhunter
sudo rkhunter -c
```

also firefox has an extension called securebrowse and another called trackmenot

---

### Post by ubuntu27 on 2008-02-10
> **jpeulen said:**
> By the way what is "OP" standing for?? "Obvious (P)idioot? :redface:  :)

OP stands for "Original Post" or  "Original Poster". It means: The person who created the thread. They are referring to you in this case ;)

---

### Post by jpeulen on 2008-02-10
I think I found the solution I was working through the South African "proxy server" called "cache.saix.net" Now I have disabled that proxy server and everything works normal. 
So to my opinion the proxy server was/is "hacked" Is that possible?

---

### Post by jpeulen on 2008-02-10
> **spiderbatdad said:**
> ```
sudo apt-get install rkhunter
sudo rkhunter -c
```

also firefox has an extension called securebrowse and another called trackmenot

With the package "rkhunter" you gave the solution to the problem. Thanks for that.

I assume that I must download that securebrowse and trackmenot from the Firefox website?

For the rest of the people also a big thanks and I am proud to be a member of such a community. This amount of help would NEVER have happened in a windows environment.

---

