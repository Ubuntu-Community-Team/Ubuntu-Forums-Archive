---
title: "Trouble with loading digital camera files from camera"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Old Jimma on 2007-04-26
Hi Ubuntuers:

I have an Olympus 4040 digital camera. I used to have no problem transfering the digital files from the camera to my Ubuntu machine, but not anymore!

Here is what happens:

I take some pictures.
I attach the camera and transfer the photos from the camera to my computer's hard disk.

THEN,
I put a NEW MEMORY CARD in my camera and take more pictures.
Then, I attach the camera to my computer.
Ubuntu can't see the new pictures on the camera's new memory card (although they are in the camera)... Ubuntu things that the old photos from the previous card are on the camera.

Hey! What is this all about?

Can somebody help me with this?

Thanks,
Phil Smith
Duluth, GA

---

### Post by AmyRose on 2007-04-26
Make sure you unmount your camera before unplugging it, if it appears as a mass storage device.  I've had this happen once in a while when I forget to unmount myself.

---

### Post by Old Jimma on 2007-05-25
Hi:

The mass storage device seems to be mounted at /media/disk . WHen I do a sudo umount -f /media/disk the camera is unmounted.

However, when I plug the camera back in, the /media/disk filesystem is mounted again, and shows old photos no longer on my camera.

What am I doing wrong?

Thanks,
Phil Smith

---

