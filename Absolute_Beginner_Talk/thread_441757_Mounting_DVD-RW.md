---
title: "Mounting DVD-RW"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-05-12
Hi,
I'm new to Ubuntu and it has installed fine and I've got my wireless and email going. I'm on an HP DV9030us laptop. 

My DVD-RW won't work however. WHen I put a CD into it, I head noise and then Ubuntu says "Cannot Mount Volume" and adds that it is invalid mount option.

Now I'm new to mounting and drivers on Linux, so if you can help me, which would be wonderful, please be as specific as you can, so I'll be clear about what I'm supposed to do.

I appreciate any help anyone could offer. Many Thanks, Frank

---

### Post by dwblas on 2007-05-12
Is this a never been used DVD.  If so it has to be initialized.  I use the following, but there are surely GUI's also.
ulimit -l unlimited
growisofs -Z /dev/hdc=/dev/zero

---

### Post by Brightbelt on 2007-05-12
My response disappeared, so I don't know what's happening. My screen and cursor are jumping around uncontrollably. Any ideas? 

I feel abandoned lately. Everyone was there to help when I was installing, but now I'm getting very curt responses.

Help someone,....Frank

---

### Post by Brightbelt on 2007-05-12
OK, I had to go to my desktop to post. My cursor and screen jumps uncontrollably when I type, so I can barely make a post. I've had my response disappear 3 times.

Now, to the DVD-RW, I have found a GUI where I can enter 'Mount point', 'File System' and 'Mount Options', but I have no idea what to put into those text fields.

I appreciate any help anyone could offer.  Thanks, Frank

---

