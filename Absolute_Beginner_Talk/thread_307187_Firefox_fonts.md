---
title: "Firefox fonts"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by QUEEN HIPPOLYTA on 2006-11-26
I know this might sound like a dumb question, but what are decent looking fonts to use on Firefox so that websites render halfway decent? I never had this issue on windows but I can't seem to get Firefox to show a font that does not look  too harsh or just plain wrong. 

Thanks in advance for being one of the most helpful sites I have used in ages :KS

---

### Post by szf on 2006-11-26
I believe that I'm using the default font: Bitstream Sans Serif.

When I started with Ubuntu, I searched these forums for a font solution because the Fedora Core side of my pc looked so much better. 

I discovered this:

Create a file named .fonts.conf (that's [dot]fonts[dot]conf) in your $HOME directory. The content of the file is:

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>

```

Logout and Login again.

---

