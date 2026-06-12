---
title: "No album art on ipod, using Amarok"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by milkaa on 2007-01-12
Hi

I have an Ipod nano 1st Generation. Works great with amarok but somehow I can't get the album art to show on my ipod. All album art is shown nicely on my Amarok page. Pls help. Thanks!

cheers
milkaa

---

### Post by petersjm on 2007-01-12
> **milkaa said:**
> Hi

I have an Ipod nano 1st Generation. Works great with amarok but somehow I can't get the album art to show on my ipod. All album art is shown nicely on my Amarok page. Pls help. Thanks!

cheers
milkaa

When you say "show nicely" on your iPod, do you mean it's there but not looking good, or it won't show at all? For me, all I have to do is drag 'n drop and everything works well. If they are there but not looking nice, maybe the quality of the album art isn't as high as it should be? Sorry, I can't think of any other reason...

EDIT: Sorry, I misread your post. You say they won't show at all... For that, I have no explanation. Sorry.

---

### Post by mahiyar on 2007-01-12
For amarok to show the album art it has to been in the same directory from which the song is being played,

---

### Post by milkaa on 2007-01-12
> **mahiyar said:**
> For amarok to show the album art it has to been in the same directory from which the song is being played,

The album art shows up on Amarok. It doesn't show on my ipod after I have transferred the songs.

---

### Post by orb9220 on 2007-01-12
He is trying to say is you have to manually look in the folder of album and see if album art jpg is there. Amarok dosn't care if it is in folder or not. It wil look up for art and put the album in it's own location not in the album folder.

---

### Post by milkaa on 2007-01-12
> **orb9220 said:**
> He is trying to say is you have to manually look in the folder of album and see if album art jpg is there. Amarok dosn't care if it is in folder or not. It wil look up for art and put the album in it's own location not in the album folder.

Hi thanks.. yes the album art jpg is in the album folder. On Amarok, it shows on the "Edit Song Information" as well. But once I transfer over to the ipod, it doesn't show on the ipod. ](*,)

---

### Post by petersjm on 2007-01-13
As an alternative, until you discover the problem, you can always use GTKPod to sync album art to your iPod.

---

### Post by enigma_0Z on 2007-02-04
gtkpod won't work if amarok won't work.

The problem is a missing/blank SysInfo file (/iPod_Control/Device/SysInfo). The fix is to compile gtkpod 0.99.8 and libgpod 0.4.0...

I put up an article on my blog here: [http://blog.pause.homelinux.net/index.php?/archives/8-Linux-+-Amarok-+-iPod-Nano-2nd-Gen-or-others-w-updated-firmware-+-WORKING-album-art.html](http://blog.pause.homelinux.net/index.php?/archives/8-Linux-+-Amarok-+-iPod-Nano-2nd-Gen-or-others-w-updated-firmware-+-WORKING-album-art.html)

---

