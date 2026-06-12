---
title: "1st gen iPod Touch will mount, but no programs will load it (anymore)"
date: 2016-01-27
forum: Apple Hardware Users
---

### Post by DaveBF on 2016-01-27
Hey,

I synced my iPod Touch (1st gen, 8gb, running os 1.1.5 (4B1) for the last time a few months ago.  Upon trying again yesterday the ipod will still mount, with its file structure readable and writable, but no program will recognize it.  I have spent hours reading forums, guides, and manuals before deciding to post here.

I'm running Ubuntu 14.04, just as I was when I last synced my iPod.  As far as I know, nothing has changed, but gtkpod tells me

```
Newly mounted iPod at '/run/user/1000/gvfs/afc:host=e565c94f061f7bf3208fdbe9569d1ef1155108b5' could not be loaded into gtkpod.
```

and Banshee says "Loading Dave's iPod" forever...

Frustrating, as I used to be able to drag and drop sync through Banshee no problem.

Any help would be nigh infinitely appreciated, as it would make my mind-numbing factory job nigh infinitely more bearable.

Thanks,
Dave

---

### Post by DaveBF on 2016-01-30
So, after going as far as installing a virtual windows within ubuntu, on which I installed itunes (it still wouldn't work with my ipod), I tried one desperate last measure that worked.

I plugged the ipod into the last windows computer that had managed it before I moved to ubuntu, and created a backup on that windows computer.  I ejected it and, upon plugging it back into my ubuntu computer, it worked!  Banshee could read and sync to it.

I figure something went wrong within the configuration files on the ipod.  To all future people having this problem, I recommend finding a windows (probably mac, too) computer to plug your ipod into.  Even a new one to format it, then bring your ipod back to ubuntu.

Cheers,
Dave

---

