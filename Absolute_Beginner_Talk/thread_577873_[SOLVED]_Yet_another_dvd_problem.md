---
title: "[SOLVED] Yet another dvd problem"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by rdsii64 on 2007-10-16
below is the output  from the grep command:
rdsii64@rdsii64-Ubuntu:~$ dpkg --list | grep libdvd 
ii  libdvdcss2                                 1.2.9-2medibuntu2+build1                Library for accessing DVDs like block device
ii  libdvdnav4                                 0.1.10-0.1                              The DVD navigation library
ii  libdvdplay0                                1.0.1-7                                 portable abstraction library for DVD menus s
ii  libdvdread3                                0.9.7-2ubuntu1                          library for reading DVDs
rdsii64@rdsii64-Ubuntu:~$ 

the problem is I still can't play an commercial dvd.  The even wierder part is that this morning 
the comming attractions played and choked on the main movie. Now when ever I put the disk in
I get a dialog box that tells me that i am trying o play a encrypted dvd with out libdvdcss.

according to  dpkg --list | grep libdvd it is there. 

HELP  I am in DVD HELL

---

### Post by Drakkor on 2007-10-16
Have you tried VLC ?

---

### Post by rdsii64 on 2007-10-16
> **Drakkor said:**
> Have you tried VLC ?

yes I have tried VLC and nothing happens.

---

### Post by yabbies on 2007-10-16
read[ this]("http://ubuntuforums.org/showthread.php?t=577072")

follow it down and if you are still having trouble then reply back

---

### Post by RomeReactor on 2007-10-16
Hi. Are you using Ubuntu 7.04 (Feisty) or 7.10 (Gutsy)? is it 32-bit or 64?

---

### Post by rdsii64 on 2007-10-16
> **RomeReactor said:**
> Hi. Are you using Ubuntu 7.04 (Feisty) or 7.10 (Gutsy)? is it 32-bit or 64?
I am using 32 bit feisty
I have also checked and rechecked everything I know. I repos seem to be in order. I have followed every tutorial I can find. the best I have ever gotten is the commin attractions will play then the menue appears. when I click play I get a dialog box that asks me if I am trying to play an encrypted dvd without libdvdcss.  The grep command shows all is present that I am aware needs to be present. VLC doesn't work, totem doesn't work, mplayer doesn't work, none of them work.
I have even tried automatrix2 and got nowhere
I have no clue what to try next.

---

### Post by RomeReactor on 2007-10-16
It sounds like you have totem-gstreamer; try switching to totem-xine:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs
```

---

### Post by rdsii64 on 2007-10-16
> **RomeReactor said:**
> It sounds like you have totem-gstreamer; try switching to totem-xine:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs
```

here is the output:


rdsii64@rdsii64-Ubuntu:~$ sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
totem-xine is already the newest version.
libxine1 is already the newest version.
libxine1-ffmpeg is already the newest version.
libxine-extracodecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rdsii64@rdsii64-Ubuntu:~$

---

### Post by mivo on 2007-10-16
RomeReactor's suggestion is what I also did a little while ago, and it works flawlessly.  You also do not have to uninstall Totem-GStreamer manually, this will be done automatically when Totem-Xine is installed (it's the much better engine, even DVD navigation works properly).

Edit: Hmm, I see it did not work for you. Odd, works here.

---

### Post by yabbies on 2007-10-16
what's the output of this command?

```
sudo apt-get install libdvdcss2
```

---

### Post by RomeReactor on 2007-10-16
Do you have the [Medibuntu repositories]("https://help.ubuntu.com/community/Medibuntu")? it looks like your libdvdcss2 is [a little outdated]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/"); if you don't have their respoitory, and installed the package by downloading it, try uninstalling it and using this [one instead]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb").

---

### Post by rdsii64 on 2007-10-16
> **yabbies said:**
> what's the output of this command?

```
sudo apt-get install libdvdcss2
```

here is the output:


rdsii64@rdsii64-Ubuntu:~$ sudo apt-get install libdvdcss2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rdsii64@rdsii64-Ubuntu:~$

---

### Post by rdsii64 on 2007-10-16
> **RomeReactor said:**
> Do you have the [Medibuntu repositories]("https://help.ubuntu.com/community/Medibuntu")? it looks like your libdvdcss2 is [a little outdated]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/"); if you don't have their respoitory, and installed the package by downloading it, try uninstalling it and using this [one instead]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb").
i uninstalled the one I had and installed the one you provided and I got an error that said dependency not satisfied

---

### Post by rdsii64 on 2007-10-16
I just made sure i had the medibuntu repos then I ran 
sudo apt-get install libdvdcss. keep your fingers crossed.

---

### Post by rdsii64 on 2007-10-16
just as before. all that plays is the coming attractions. When the main movie starts nothing
just a dialog box say that I am trying to play an encrypted dvd then nothing

---

### Post by yabbies on 2007-10-16
Is it only with that DVD?
I will check back later
Gotta split

---

### Post by m9ke on 2007-10-16
Different DVDs have different encryption ranging from none to pretty strong.

Try a range of DVDs with each change you make, if you've not already done so.

---

### Post by rdsii64 on 2007-10-16
> **m9ke said:**
> Different DVDs have different encryption ranging from none to pretty strong.

Try a range of DVDs with each change you make, if you've not already done so.


I tried to play the Omega code and it played just fine. tried to play the guardian and I get the same stuff i have been getting all day.

---

### Post by rdsii64 on 2007-10-16
> **m9ke said:**
> Different DVDs have different encryption ranging from none to pretty strong.

Try a range of DVDs with each change you make, if you've not already done so.

tried it again with madagascar and no dice. the comming attractions and nothing else

---

### Post by m9ke on 2007-10-17
I have seen something kind of similar.  

If the backup DVD does not play past the previews automatically when you insert it, look at the actual files on the backup DVD and see if you can play them by double clicking them.  

This won't be a solution to the problem, but if you can play these files manually, it at least shows they made it to the back up.

Also I have seen that just because a backup won't play on my computer does not mean it won't play on my DVD player that's hooked up to the tv.  Just for grins, try it that way if you can.

EDIT:  I have also seen backups that *would* play on my Windows box using WinDVD that would not play on my Linux box using Totem.

In all these cases, I saw the DVD Main Menu on the TV or on WinDVD under Windows, but my Linux box did not show it.  I couldn't get past the first part of t he backup (in your case the previews) because I couldn't see the menu to select the next segment.

Dont know if this will help you--I don't know much about this topic and I hope others will chime in.

---

### Post by m9ke on 2007-10-17
I got curious about this and performed the following experiment.

1-Took a new DVD which is encrypted and which I own, and made one backup copy using K3b

2-Played the backup on my Ubuntu box (Feisty) using Totem, on my home DVD player, and on my Widows  box.
2a-Result:  On my Ubuntu box the backup played the the introductory crap, but showed only a black screen when it should have shown the DVD main menu.
2b-Result:  I played the same backup on my home DVD player hooked to my TV set.  It showed the DVD main menu and could play everything on it.  (worked as expected)
2c-Result: I played the same backup on my Windows box  using WinDVD.  It worked as expected.

3.  Played the original factory DVD on my Ubuntu box (Feisty) using Totem, on my home DVD player, and on my Widows  box.
3a-Result: On my Ubuntu box the factory original played the the introductory crap, but showed only a black screen when it should have shown the DVD main menu.
3b-Result:  I played the same factory original on my home DVD player hooked to my TV set.  It worked as expected.
3c-Result: I played the same factory original on my Windows box  using WinDVD.  It worked as expected.

Conclusion for my issue anyway:  this is a playback problem on my Ubuntu box, not a backing up problem, as evidenced by the fact that the original and the backup gave identical results when played in 3 different locations.

I still don't know if this is any help, but it might be interesting to see if the backups that won't play on your Linux box behave differently elsewhere.

---

### Post by m9ke on 2007-10-17
Solved the playback problem by installing libxine and related packages.  This un-installs gstreamer.  Previously I was running totem-gstreamer, now totem-xine.

More here
[http://ubuntuforums.org/showthread.php?t=396738&highlight=totem+dvd+main+menu](http://ubuntuforums.org/showthread.php?t=396738&highlight=totem+dvd+main+menu)

Apologies---Just realized I got carried away looking at this and hijacked this thread!

---

### Post by rdsii64 on 2007-10-18
> **m9ke said:**
> I got curious about this and performed the following experiment.

1-Took a new DVD which is encrypted and which I own, and made one backup copy using K3b

2-Played the backup on my Ubuntu box (Feisty) using Totem, on my home DVD player, and on my Widows  box.
2a-Result:  On my Ubuntu box the backup played the the introductory crap, but showed only a black screen when it should have shown the DVD main menu.
2b-Result:  I played the same backup on my home DVD player hooked to my TV set.  It showed the DVD main menu and could play everything on it.  (worked as expected)
2c-Result: I played the same backup on my Windows box  using WinDVD.  It worked as expected.

3.  Played the original factory DVD on my Ubuntu box (Feisty) using Totem, on my home DVD player, and on my Widows  box.
3a-Result: On my Ubuntu box the factory original played the the introductory crap, but showed only a black screen when it should have shown the DVD main menu.
3b-Result:  I played the same factory original on my home DVD player hooked to my TV set.  It worked as expected.
3c-Result: I played the same factory original on my Windows box  using WinDVD.  It worked as expected.

Conclusion for my issue anyway:  this is a playback problem on my Ubuntu box, not a backing up problem, as evidenced by the fact that the original and the backup gave identical results when played in 3 different locations.

I still don't know if this is any help, but it might be interesting to see if the backups that won't play on your Linux box behave differently elsewhere.

My back ups play fine on my ubuntu box. the difference may be that my back ups on contain the main movie and nothing else

---

### Post by rdsii64 on 2007-10-18
> **m9ke said:**
> Solved the playback problem by installing libxine and related packages.  This un-installs gstreamer.  Previously I was running totem-gstreamer, now totem-xine.

More here
[http://ubuntuforums.org/showthread.php?t=396738&highlight=totem+dvd+main+menu](http://ubuntuforums.org/showthread.php?t=396738&highlight=totem+dvd+main+menu)

Apologies---Just realized I got carried away looking at this and hijacked this thread!
read that and followed instructions to the letter with out results.

---

### Post by m9ke on 2007-10-19
> I tried to play the Omega code and it played just fine. tried to play the guardian and I get the same stuff i have been getting all day.

> tried it again with madagascar and no dice. the comming attractions and nothing else

Is the Omega Code DVD that played fine an original or a backup?
Are the Guardian and Madagascar DVD that only played the previews originals or backups?
Do you have another computer you can try Guardian and Madagascar DVDs on?
Do you have a DVD player connected  to your tV you can try the Guardian and Madagascar DVDs on?

The intent of these questions is to isolate the problem.  This problem might be in the DVDs themselves, or in the hardware you are trying to play them on.

---

### Post by rdsii64 on 2007-10-19
> **m9ke said:**
> Is the Omega Code DVD that played fine an original or a backup?
Are the Guardian and Madagascar DVD that only played the previews originals or backups?
Do you have another computer you can try Guardian and Madagascar DVDs on?
Do you have a DVD player connected  to your tV you can try the Guardian and Madagascar DVDs on?

The intent of these questions is to isolate the problem.  This problem might be in the DVDs themselves, or in the hardware you are trying to play them on.
the guardian and madagascar are originals. The strange part is so was the Omega code.
I even put the omega code in my windows box and verified that it was an encrypted dvd.
I did this by starting up dvd shrink and looking for the decryption key. Sure enough Omega code is an encrypted dvd.

---

### Post by rdsii64 on 2007-10-19
> **m9ke said:**
> Is the Omega Code DVD that played fine an original or a backup?
Are the Guardian and Madagascar DVD that only played the previews originals or backups?
Do you have another computer you can try Guardian and Madagascar DVDs on?
Do you have a DVD player connected  to your tV you can try the Guardian and Madagascar DVDs on?

The intent of these questions is to isolate the problem.  This problem might be in the DVDs themselves, or in the hardware you are trying to play them on.
the guardian played in my set top player and on my windows box. I haven't tried madagascar anywhere else yet.

---

### Post by guitodd on 2007-10-19
Follow these instructions and set-up VLC.  It works like a champ!  

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

---

### Post by rdsii64 on 2007-10-19
> **guitodd said:**
> Follow these instructions and set-up VLC.  It works like a champ!  

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)
Already have VLC installed got from the same place you recommended and got no results

---

### Post by rdsii64 on 2007-10-20
I just wiped my system clean and installed 7.10, I will try to go at it again in the morning.
with a fresh install of gutsy I may have better luck

---

### Post by m9ke on 2007-10-20
It looks to me like it's a playback problem on your Ubuntu box, given that the problem DVDs are originals.  

I am pretty sure you will need to install some more plugins after your clean install.  

If it was me, I would do exactly what you are doing, then I 'd pick just one thread of advice for playback and follow it to the letter as you have been doing all along.  That way your box is in a known state.

This is frustrating I know but I can see from the number of views on your post that a lot of people are reading and probably learning, so hang in there.

Please post your results.  

Cheers,
m9ke

---

### Post by amlucent23 on 2007-10-20
Although this covers enabling dvd playback in Gusy not Feisty I still think it may be of use for someone with a similar problem reading through your post. Its a video how to.


[URL="http://screencasts.ubuntu.com/Watching_Video"]
http://screencasts.ubuntu.com/Watching_Video[/URL]

---

### Post by rdsii64 on 2007-10-20
> **amlucent23 said:**
> Although this covers enabling dvd playback in Gusy not Feisty I still think it may be of use for someone with a similar problem reading through your post. Its a video how to.


[URL="http://screencasts.ubuntu.com/Watching_Video"]
http://screencasts.ubuntu.com/Watching_Video[/URL]

got my gutsy install up and running. I just put an original copy of united flight 93 in and it seemed to play ok. I tried madagascar one more time and got the same result. I am not sure but maybe the madagascar disc is bad, scratched or what ever.
I will try a few other DVD's to comfirm all is ok. 
Not sure why but wiping my machine and doing a gutsy install seemed to fix what ever was wrong.
I just installed automatrix2 and all seems fine so far.keep your fingers crossed.

---

### Post by rdsii64 on 2007-10-20
> **m9ke said:**
> It looks to me like it's a playback problem on your Ubuntu box, given that the problem DVDs are originals.  

I am pretty sure you will need to install some more plugins after your clean install.  

If it was me, I would do exactly what you are doing, then I 'd pick just one thread of advice for playback and follow it to the letter as you have been doing all along.  That way your box is in a known state.

This is frustrating I know but I can see from the number of views on your post that a lot of people are reading and probably learning, so hang in there.

Please post your results.  

Cheers,
m9ke

well with mplayer the main movie plays and the coming attractions are MIA ( missing in action) I am fine with that. I took the disc and put it in my windows box to confirm it is an encrypted DVD. I did this by firing up dvd shrink and looking for the decryption key. I was able to confirm that united flight 93 is an encrypted disc. so far it plays with out any issues. 

I think my problem is solved but I won't confirm until I have tried a variety of origonal discs

---

### Post by m9ke on 2007-10-20
Glad to see things are looking up.  If you don't  care about the previews and DVD menus, then you are making real progress.  Maybe that one disc that won't play is damaged as you suggested or maybe it has different encryption.

Let us know how it goes.  I will watch this thread until you mark it solved.

PS also glad to hear your Gutsy install went well!

Cheers,
m9ke

---

### Post by rdsii64 on 2007-10-25
well it is confirmed now that what ever my DVD problem was in 7.04 has been solved by doing a clean install of 7.10. on one hand I am glad my problem is solved, on the other hand I would love to know what the problem was. Anyway 7.10 runs as smoothly as it can considering the modest hardware I have to work with. I am running a paltry 16meg video card and dvd movies play smooth with no glitches or dropped frames during fast motion. 

all in all, color this one solved.

---

