---
title: "A sudo problem"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by darsu on 2006-05-25
I may just be having a temporary blackout and the answer is completely obvious, and/or I may be locked in an erroneous mindset due to having only recently migrated from a distro with a *root*, but:

In the midst of setting up some Asian fonts for Java, I type "sudo ttmkfdir > fonts.dir" in /usr/lib/j2(blah)/fonts. It refuses to work:
"bash: fonts.dir: Permission denied."

This looks incomprehensible. Is there something I'm not getting, or is sudo so stupid that the piping of the command output into a file is outside the scope of my temporarily being superuser? How is what I'm trying to accomplish done properly with sudo?

Fonts.dir exists and has permissions 644, ./ has 755. Yes, I can solve this by changing the perms, but that is not a sustainable solution.

---

### Post by Steggy on 2006-05-25
I believe you need to sudo after the ">" also

---

### Post by mlind on 2006-05-25
use either

sudo sh -c "ttmkfdir > fonts.dir"
or
sudo ttfmkdir | sudo tee fonts.dir

---

### Post by darsu on 2006-05-25
All right, thanks.

---

