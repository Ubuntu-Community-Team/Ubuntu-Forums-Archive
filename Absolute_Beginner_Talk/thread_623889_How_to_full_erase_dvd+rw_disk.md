---
title: "How to full erase dvd+rw disk?"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Ux64 on 2007-11-26
How to full erase dvd? Because I was going to start a new thread about that.

Brasero seems to only quick erase dvd. So does dvd+rw-format. Is there any way to do complete (full) erase?

Because without full erase burn quality is so poor that it might be impossible to read disk after writing. If I do full erase, with my windows computer, than I can burn disk perfectly. But how I can do full erase with linux / ubuntu / brasero?

- Thank you!

Ubuntu 7.10 GG 64 bit, Brasero 0.6.1, dvd+rw-format 0.7

---

### Post by prodigalson666 on 2007-11-26
Install K3B, it has more options than any other burn program out there I've seen so far, one of the options includes format for dvd,cd, this is the longer version instead of the quick erase you are talking about.

---

### Post by skymera on 2007-11-26
i double K3B, it is the most sophisticated software ive ever used for CD+DVD burning, 
and straight from repos.

it has options to erase diskys :)

---

### Post by Sorken on 2007-11-26
Are you sure you did format the disk with dvd+rw-format? Not just blank the disk.

It should be &#314;ike this
> dvd+rw-format -force=full /dev/dvd

For dvd+rw you can also try
> wodim -format

---

### Post by FuturePilot on 2007-11-26
I believe Gnomebaker can do a complete erase.

---

### Post by Ux64 on 2007-12-03
> **Sorken said:**
> Are you sure you did format the disk with dvd+rw-format? Not just blank the disk.

I tried. But it doesn't seem to be working .Quick erase still works.

```

~$ dvd+rw-format -force=full /dev/dvd
* BD/DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
* 4.7GB DVD+RW media detected.
- unimplemented command-line option for this media.
- you have the option to re-run dvd+rw-format with:
  -lead-out  to elicit lead-out relocation for better
             DVD-ROM compatibility, data is not affected;
  -force     to enforce new format (not recommended)
             and wipe the data.

```

And -force means only to quick erase... 

```

~$ dvd+rw-format -force /dev/cdrom
* BD/DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
* 4.7GB DVD+RW media detected.
* formatting 98.6-

```

And it works. But doesn't produce results which I need as I described earlier.

Next question:

How to format (I thought that format tool would allow to format disks) packet writing disks?

Ubuntu seem to support those disks directly if I format one with Windows Vista. But how I can format disk using Ubuntu?

- Thanks

---

### Post by rfurman24 on 2007-12-11
I think I have the same problem. I have burned to a dvdrw and now need to erase. If I use the format command I still can not burn to the dvd likewise if I use k3b and do full format the disc is not even recognized.

---

### Post by rfurman24 on 2007-12-12
I finally was able to burn to the disc using the nautilus burning utility.

---

### Post by Ux64 on 2007-12-18
> **rfurman24 said:**
> I finally was able to burn to the disc using the nautilus burning utility.

Ok, you burned it. But were you able to full erase that disk before burning it?

And when burning failed, was it because system said that disk isn't empty. Or write quality was so bad you couldn't read disk anymore?

I have quality problem without full erase and that's why I'm looking for way to do full erase instead of quick erase.

---

### Post by CCNA_student on 2007-12-18
You should be able to just download Gnomebaker or K3B, and erase your disks with one of those programs. You could always use Kubuntu instead of Ubuntu also. I just think that KDE is better than Gnome. I hope that this helps you. 

    Sin Cere,

    CCNA_student

---

### Post by rfurman24 on 2007-12-18
> **Ux64 said:**
> Ok, you burned it. But were you able to full erase that disk before burning it?

And when burning failed, was it because system said that disk isn't empty. Or write quality was so bad you couldn't read disk anymore?

I have quality problem without full erase and that's why I'm looking for way to do full erase instead of quick erase.

When I double clicked the iso I wanted to burn, the nautilus burner popped up and said the disk was full and asked to erase it. I said yes and it did it and then continued the burn. The disk plays fine. When using k3b or command line to erase it would not work for me.

---

### Post by Cannaregio on 2007-12-24
I had huge problems with my DVD+RW: couldn't erase them with gnomebaker, couldn't erase them with K3B, couldn't erase them with brasero.
Couldn't erase them in windows neither, nor with nero, nor with alcohol120.

The only thing that worked was, with linux:
```
sudo dvd+rw-format -force  /dev/dvd

```

This, and only this, did the job for me.


I believe this problem is mainly due to the low quality DVD writers we use, in my case an Hewlett Packard HP dvd writer 740b.

---

### Post by rfurman24 on 2007-12-24
For some reason the nautilus burning tool has started flaking out and k3b now works fine. I noticed after a bunch of updates but I did not check to see what they were.

---

