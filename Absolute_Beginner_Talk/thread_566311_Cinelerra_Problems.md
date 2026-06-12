---
title: "Cinelerra Problems"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-10-03
Hi,

Whenever I start Cinelerra I get the following error :

> MWindow::init_shm():Warning: /proc/sys/kernel/shmmax is 0x2000000, which is too low.
Before running Cinelerra do the following as root:
echo "0x7fffffff" > /proc/sys/kernel/shmmax

I have been trying to run the above command from terminal but everytime the message is permission denied.
I tried with > sudo su and then run the command. But the result is the same > "Permission denied". chmod also does not change the permissions.

can someone help me here?

---

### Post by por100pre1 on 2007-10-03
Use this method, as suggested in the [Cinelerra page]("http://cvs.cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_21.html#SEC296").

```
sudo cp /etc/sysctl.conf /etc/sysctl.conf_backup
```

```
sudo su -c 'echo kernel.shmmax = 2147483647 >> /etc/sysctl.conf'
```

```
sudo sysctl -p
```

Hope this helps. :)

---

### Post by Samhain13 on 2007-10-03
Disclaimer: Not An Expert.

1. Become root: "sudo -i", input your password
2. The run: echo "0x7fffffff" > /proc/sys/kernel/shmmax

...at least that's what I did. :D

If you don't want to do this every time you start your computer,
do what por100pre1 says.

Cheers!

---

### Post by Toadmund on 2007-10-11
Yes, do what the OP says.

OK, I have a problem.
How do I add a new track without pasting over the other tracks?

I have 2 tracks for video (1 video track, 1 audio)
I want to add an additional 3rd music track, but it writes over the previous 2.

I am stuck on that problem at the moment, help would be most awesome ](*,)

OK, I just dragged it over from 'resources', that worked.

Carry on, nothing to see here people.

OK people, how do I edit just ONE track? Seems the vertical line affects all tracks, how do I choose just one?

---

### Post by eldragon on 2007-10-11
ok, to get you right out of your problem

you need to disarm the tracks you wont be editing......

thats the record button on the left (each track has one).


so.......just arm (record) the track you want to modify and start pasting.. :)


some great guide to cinelerra (and video) is being given by the guys behind 'the_source'

download their shows.......right now you got: 
episode 6: includes the first of the guides. brings the basics,
episode 1: has the second guide in it. talks about the different ways to edit (drag/drop, cut and paste)
episode 2: last guide available, talks about effects..

thers a promised fourth guide about rendering....not released yet.

hope i helped.

---

### Post by Toadmund on 2007-10-11
You certainly did help :)

2 more problems.

-One with de-synchronization of video with sound. (a bit-rate thing?)

-I also have sound spikes, a static like 'CHITT' sound, that occurs regularly, every 20 seconds or so.

Thanks again!

---

