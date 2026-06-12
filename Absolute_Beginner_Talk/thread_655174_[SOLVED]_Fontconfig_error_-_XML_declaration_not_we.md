---
title: "[SOLVED] Fontconfig error - XML declaration not well-formed"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by abcuser on 2008-01-01
Hi,
on Ubuntu 7.10 when executing gedit command from Terminal, gedit is executed successfully but I get error in Terminal:

Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

I have look into the .fonts.conf file which looks like this:
> <?xml version="1.0&#8243; ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
<edit name="autohint" mode="assign">
<bool>true</bool>
</edit>
</match>
</fontconfig>

If I remove first line from file the error disappears. What is wrong with first line?

Thanks,
Abcuser

---

### Post by abcuser on 2008-01-01
Hi,
solved the problem. I just copied first two rows from web page:
[http://ubuntuforums.org/archive/index.php/t-472208.html](http://ubuntuforums.org/archive/index.php/t-472208.html)

Problem solved.
Thanks,
Abcuser

---

