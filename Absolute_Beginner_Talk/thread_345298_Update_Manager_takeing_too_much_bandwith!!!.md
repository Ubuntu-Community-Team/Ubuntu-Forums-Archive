---
title: "Update Manager takeing too much bandwith!!!"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Phototrek1 on 2007-01-24
Hello,
I have a small problem.  I use dial up and the update manager application takes up all the bandwith.  I'm unable to use the internet because of it.  Is there a way to limit how much bandwith it uses.  I like downloading things at 1kbps because there isn't any noticeable degration in bandwith.

Thanks 
Phototrek1

---

### Post by zerhacke on 2007-01-24
[http://www.techiesabode.com/show/show_tips_w.php?tip_id=72](http://www.techiesabode.com/show/show_tips_w.php?tip_id=72)

---

### Post by Phototrek1 on 2007-01-25
Do i just cut and past the directions and is it permnant?

----------------------------------------------------------------------------
#!/bin/bash
cd /var/cache/apt/archives || {
	echo Failed to change to /var/cache/apt/archives >&2
	exit 1
	}

apt-get -f -y update
apt-get --print-uris -d -y dist-upgrade | grep "^'" | while read uri x; do
		# filter out all but the URIs with the grep
		# grab just the first arg
		uri=${uri#'}; uri=${uri%'};
		# trim the leading and trailing quotes from the URI
		wget --limit-rate=5k "$uri"
		done
----------------------------------------------------------------------------------

Thanks,
Phototrek1

---

