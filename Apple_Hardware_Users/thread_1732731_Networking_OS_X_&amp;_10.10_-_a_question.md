---
title: "Networking OS X &amp; 10.10 - a question"
date: 2011-04-18
forum: Apple Hardware Users
---

### Post by pedrogent on 2011-04-18
I have an Ubuntu 10.10 'server/NAS' that I have hooked up to my MacBook 5,2. I have a few directories on the Ubuntu box shared using AFP. I've installed netatalk and avahi-daemon in order to facilitate this.

One of the directories on the Ubuntu box is /media/data. This is shared. It has four sub-directories, one of which is /media/data/photos.

Does anyone know why, then, on the MacBook side I have the option to mount *both* /media/data & /media/data/photos?

Another way of asking this would be to say, why aren't the remaining three subdirectories:

[LIST]
[*]/media/data/audio
[*]/media/data/software
[*]/media/data/video
[/LIST]

also available to mount discreetly?

Is this something to do with file permissions?

I don't want to have the option to mount just /media/data/photos, so where should I be looking for configuration files to alter so that only /media/data is offered up to be mounted?

Thanks.

EDIT: I solved this problem by doing gksu nautilus and unsharing /media/data/photos from there. That partition is owned by root.

---

