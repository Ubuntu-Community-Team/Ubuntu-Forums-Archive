---
title: "Converting lots of ape to flac?"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-01-24
Ok so my method of converting all my ape files from my old windows days is this.

```

mac "sample.ape" "sample.wav" -d
flac sample.wav
rm sample.wav
rm sample.ape

```

My problem is that I have lots of ape files. In the order of hundreds. Also I would like to keep the tag information.

This works for the flac part

```
flac *.wav
```

but this does not work

```
[COLOR="Red"]mac *.ape *.wav -d[/COLOR]
```

I was thinking that maybe I could use a script. In that case how would I go about that?

The reason I want flac is because they play better over my NFS shares, and I've got a cool new IAUDIO mp3 player that can play flacs.

---

### Post by guysmiley25 on 2007-01-24
Anyone?

---

### Post by turbojugend_gr on 2007-01-24
mac *.ape *.wav -d ----> m8 that is never gonna work, ofcourse, you are giving it no destnation name that is why. See when you say flac *.wav you are actually telling it to keep the main name of all the files that end in *.wav, it does not understand they are wav files, it is only a method for it to select the files. In the second case though you are wrong cause mac needs a destination filename and you provide this as *.wav, which is ot acceptable. The only way I can think for you to do this is a script, indeed. Though give a the man page a chance, maybe there is a solution in there (man mac is the command).

For the script ----> Open a text editor and type :
> !#/bin/bash that will inform the system of the language you are using in the script, so it can use the appropriate "tool" to translate it, actually that is the tool there, anyway continue with your scrpt with a for then stanza, though remebmer to retrieve the number of the repetitions needed, a way to do that is to insert > ls -1 |wc -l that will export the number of files in the current catalogue, save this output as a variable, then use it at the "for then" stanza. I hope I helped... If you need any more help say so.

Best Regards, TJ.

---

### Post by guysmiley25 on 2007-01-25
Ok I have done a very little scripting. But I've done some programming in the past. So I think I get what your talking about.

In "madeup code"

```

count = ls -1 |wc -l

x = 0

For x = 1 to count
  x = x + 1
  mac "track" + x + ".ape track" + x + ".wav -d"
Next

flac *


```

Would that Idea work or would I need to add the flac part to the loop?

Although this is a good starting point, I'm not too sure if this will work how I want. The naming of the files are in the form "Artist - Title.ape". Also my directory is lay outed in the form of "Lossless/Artist - Album/Artist - Title" where some are ape and some are flac. This is not really much of a problem since I do not mine doing each album manually it was mainly the thought of doing each song!

Thanks for the help so far turbojugend

---

### Post by guysmiley25 on 2007-01-25
Oh and ID tags are also important to me.

I don't ask too much do I? :D

---

### Post by yabbadabbadont on 2007-01-25
[convtoflac script](http://www.legroom.net/modules.php?op=modload&name=Open_Source&file=index&page=software&app=convtoflac)

and

[http://gnormalize.sourceforge.net/](http://gnormalize.sourceforge.net/)

Both look like they will do what you want.

---

### Post by turbojugend_gr on 2007-01-25
> **yabbadabbadont said:**
> [convtoflac script](http://www.legroom.net/modules.php?op=modload&name=Open_Source&file=index&page=software&app=convtoflac)

and

[http://gnormalize.sourceforge.net/](http://gnormalize.sourceforge.net/)

Both look like they will do what you want.
Lol It's true I should have googled it before suggesting scripting it (it6 is only that I enjoy it more, if it's mine... ;))

Hope you got your job done with that script m8, if not let me know, your script is close anyway.

---

### Post by jeremy on 2007-01-25
Not sure about the ape to flac bit. I use soundKonverter which I think will do it, and when I do flac to ogg it preserves the id3 tags. When I have files without the tags, I use EasyTAG to add them quick and easily. Both these programmes are in the repos.

---

### Post by guysmiley25 on 2007-01-25
Thanks guys, that has helped alot. I feel like using one of those scripts just to get the job done, but I think I will keep working on the script I started with turbojugend_gr. Just for the experience. I've got a few other script project I want to do so this will be a good first.

EasyTAG looks like the way to go with tags. I wonder if there is a text based version that I could add to my script?

Does EasyTAG get information from a database based on what it may already know, maybe based on filename and track length?

I'm quite fussy when it comes to my music collection. I have it organized quite well from the very start and done all my own tags. This is why I would rather copy the information instead of getting else where. But if it will have to do so be it.

So yes turbojugend_gr I would like to carry on with my own scripts. And all help from you and every one else has been excellecne. These forms are awesome.

---

### Post by turbojugend_gr on 2007-01-25
Hehe, he is one of us, Stuborn! ;)

Well here is how I would progress with this, I would copy (not move) three of my song files, the more diverse the group is the better, and create a script-test folder for them, in there I would try the script, and add a -v (verbose) parametre to see what is wrong (cause for quite some time there will be sth always going wrong...).

The script so far does not look that good, I don't see it reading any input on the filename neither determining the relative output.... hm try reading the first script yabbadabbadon't suggested, after all that is the power of OSS, one can learn from another dev ;). That one is very well written and as quotes so it could be helpful to you, bardon me but I am taking my uni exams these days so I ain't got much time... :(

I really like your attitude guysmiley25, I like doing small tasks myself, it is satisfying, like painting sth... anyway the thing is that this one might end up being a complicated case though.... try plaiying with that script of yours (yes you have to point out it is flac, so put that in) the way I suggested above, see if it has any potential, if not ,learn from the good script yabbadabbadont suggested.

I would really lke to participate, but damn I ain't got time.... maybe next time you need sth we may end up creating a script.... 


My best Regards, TJ.

---

### Post by guysmiley25 on 2007-01-26
Chears for the pointers turbojugend_gr. You have been very helpful.

I understand about the uni exams, I too am a uni student. I'm not studying over then summer though :), But have been working a lot of over time :(. What is it that you are studying? I have not decided what degree or major I am going to do, but last year I did some Math, Phys, and Comp papers.

I was wondering if you get a chance help me with this small problem for an other project?

I have a small scripting problem. What I want to do is run two programs from a script one after the other but I do not want the second one to wait for the first one to finish.

eg
```

!#/bin/bash
program one
prgram two
exit

```

Where program one starts then program two starts. Then afterward either/or/both programs finish on there own accord.

---

### Post by turbojugend_gr on 2007-01-26
> !#bin/bash

program1 & program2


**((((((((( ** options:   *&&* will w8 for the first one to exit then begin the second app. use *sleep 12* and the second app will start 12 seconds after the first one starts... ---> 
> 

!#/bin/bash

app1
sleep 1
app2

---> this way the 2nd app will start one second after the first one starts... ;)                      **))))))))))))))**

For any further questions say so..

Cheers, TJ.

---

### Post by guysmiley25 on 2007-01-26
Sorry I don't think I asked the question right. Either that or it did not work :-k

What I want to do is run two applications at the same time.

So if I had firefox and amsn. I would want firefox to open, then amsn. And not have to wait for firefox to be closed for amsn to be started. The effect of having two terminal sessions.

Is what I'm asking doable? If so I think it's because I don't really know what its called! multitasking?

Chears for that sleep command turbojugend_gr thats going to help me with other projects also. :)

---

### Post by yabbadabbadont on 2007-01-27
> **guysmiley25 said:**
> Sorry I don't think I asked the question right. Either that or it did not work :-k

What I want to do is run two applications at the same time.

So if I had firefox and amsn. I would want firefox to open, then amsn. And not have to wait for firefox to be closed for amsn to be started. The effect of having two terminal sessions.

Is what I'm asking doable? If so I think it's because I don't really know what its called! multitasking?

Chears for that sleep command turbojugend_gr thats going to help me with other projects also. :)

When you start the first app, add an & at the end of the line so that the application launches in the background.  The script will then proceed to the next command without waiting for the first to exit.

---

### Post by turbojugend_gr on 2007-01-27
lol--- m8 sorry it was kinda late when I gave the answer.... thus I forgot to press the return key.. the second app is supposed to be at the line below.... so sth like

> app1 &
app2
or
> app1 &
sleep NUMBER_OF SECONDS_DESIRED
app2

EDIT : Hmmm I must cut on my drinking, before I suggest sth even worse, from what I see I did think wrong on the sleep example too, maybe I didn't think str8 at all, anyway these examples should do it.

---

### Post by turbojugend_gr on 2007-01-27
> **yabbadabbadont said:**
> When you start the first app, add an & at the end of the line so that the application launches in the background.  The script will then proceed to the next command without waiting for the first to exit.

Oh ok I saw this now, gd gd, so at least you didn't w8 long... ;)

Cheers M8s, TJ.

---

### Post by guysmiley25 on 2007-01-27
Thanks heaps for that  yabbadabbadont and turbojugend_gr. That did solve my problem. I was just wondering if I where using a command line system and did something like this.

```

sudo aptitude upgrade &

```

Then I could continue to do things while that was happening! Is this wise? Also could I do such a thing and then logout? Maybe start a download then logout then off to work.

```

wget http://coolstuff.com/my/cool/download.blue &

```

Then logout.

Anyway I was wondering if I could get some pointers on editing files from a scripts. I'm working on a script that will setup my system the way I like for a reinstall, and so I do not have to manually setup all my computers.

My computers will vary in step and a bit being different hardware, and different purposes.

An example would be setting up numlockx to be turned on at startup via [this]("http://ubuntuforums.org/showthread.php?t=16891") gudie.

Another would be to configure grub. Change boot options, Timeout, etc.

Thanks heaps so far.

---

### Post by yabbadabbadont on 2007-01-27
As for your aptitude example, just open a new terminal, a new tab in the current terminal, or switch to a different console session...  :D

As for logging out, unless you start the process with nohup ("man nohup" for details), any process started by that shell (or terminal) will be killed when the shell exits.

---

### Post by guysmiley25 on 2007-01-29
Chears yabbadabbadont. That will come in handy.

Any ideas of editing a text file from a script?

---

### Post by yabbadabbadont on 2007-01-29
> **guysmiley25 said:**
> Chears yabbadabbadont. That will come in handy.

Any ideas of editing a text file from a script?

man sed
man awk
man grep

:D

---

### Post by ajm2005 on 2007-02-04
> **guysmiley25 said:**
> Ok so my method of converting all my ape files from my old windows days is this.

```

mac "sample.ape" "sample.wav" -d
flac sample.wav
rm sample.wav
rm sample.ape

```

My problem is that I have lots of ape files. In the order of hundreds. Also I would like to keep the tag information.

This works for the flac part

```
flac *.wav
```

but this does not work

```
[COLOR="Red"]mac *.ape *.wav -d[/COLOR]
```

I was thinking that maybe I could use a script. In that case how would I go about that?


an alternative to a script is to use shntool - see:

[http://aidanjm.wordpress.com/2007/02/04/converting-monkey&#8217;s-audio-ape-files-to-flac-in-ubuntu/](http://aidanjm.wordpress.com/2007/02/04/converting-monkey&#8217;s-audio-ape-files-to-flac-in-ubuntu/)

---

### Post by sp200606 on 2007-05-05
Could anyone point to me where to find "mac" - I can't find it!

Thanks

---

### Post by yabbadabbadont on 2007-05-05
> **sp200606 said:**
> Could anyone point to me where to find "mac" - I can't find it!

Thanks

The sourceforge page for mac-port doesn't seem to exist any longer....  however, there is a "jmac" project on sourceforge that claims to be a java implementation of a monkey audio encoder/decoder.  Perhaps you can use it instead?

---

### Post by ajm2005 on 2007-06-17
> **sp200606 said:**
> Could anyone point to me where to find "mac" - I can't find it!

Thanks

the project appears to have been removed from source forge..

---

### Post by regomodo on 2007-06-26
[http://members.iinet.net.au/~aidanjm/mac-3.99-u4_b3-1_i386.deb](http://members.iinet.net.au/~aidanjm/mac-3.99-u4_b3-1_i386.deb) is the mac-port i think )monkeys audio)

i followed this guide [http://aidanjm.wordpress.com/2007/02/04/converting-monkey%E2%80%99s-audio-ape-files-to-flac-in-ubuntu/](http://aidanjm.wordpress.com/2007/02/04/converting-monkey%E2%80%99s-audio-ape-files-to-flac-in-ubuntu/) 

seems to work although soundkonverter gets its completion times all out of wack

---

