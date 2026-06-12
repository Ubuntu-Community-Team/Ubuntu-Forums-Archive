---
title: "X-server crash! (messed up xorg.conf and now can't get graphical interface)"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by Gimbo on 2006-02-15
I was trying to change the color depth, so I edited the xorg.conf file at /etc/X11/

When I next booted up, I got various error messages related to X-server, which gave me the option to show error logs and such. I had a quick look at these but none of it made any sense to me. It now dumps me in a text-only environment, as if I'd done a server install or something.

I tried editing the xorg.conf file back to its original state using vi, but that doesn't seem to have been successful. The comments at the top of the file suggest there's some way of automatically updating it:

```
sudo dpkg-reconfigure -phigh xserver-org
```

I tried this, but it told me it wasn't installed :???: 

Any help getting back to where I was would be really great. Is there some way I can reinstall X-server or automatically generate a new xorg.conf file?

---

### Post by barbarossa on 2006-02-15
I think this should be:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Gimbo on 2006-02-15
Cheers - I'll try that.

---

### Post by Gimbo on 2006-02-15
Success! I'm now back to normal. Thanks very much for the help.

In my case, the solution was:

```
sudo dpkg-reconfigure xserver-xorg
```
- Go through the options, tweaking as necessary until you get X server back.
- When you get back to your desktop, if things look a bit shaky, check the xorg.conf file looks reasonable and then restart. Things should go back to normal.

---

