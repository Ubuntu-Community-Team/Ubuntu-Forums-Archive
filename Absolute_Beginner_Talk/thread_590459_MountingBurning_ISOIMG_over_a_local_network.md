---
title: "Mounting/Burning ISO/IMG over a local network"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by meighty on 2007-10-24
I've been searching the forums and the net for awhile now but I can't seem to find my answers. I'm looking for a way to...

1. Mount an image on my gutsy box that is on a file storage server. This is all via my local network. I have no problems mounting the image if its local.

2. Burning said image via the network without having to first copy the image to my local disk. Again, burning them once they are here, ain't no thing. 

Thoughts?

Thanks!
Adam


EDIT: Afterthought...I've installed k3b and k3b lets me browse the network but once i go to burn it says that it can't fine the image. 

Cheers!

---

### Post by meighty on 2007-10-24
Well after talking with some friends we came to find out, that I was connecting to my ubuntu server via samba and a smb share won't let me burn/mount any ISOs. So all i had to do was install and config NFS, mount the NFS share, and then i'm ready to rock and/or roll.

:guitar:
metal...

---

