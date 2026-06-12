---
title: "Installation problems on kubuntu"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by LucMeister on 2007-06-09
i cannot seem to get matlab student version 7 release 14 sp3 to install on kubuntu.

i have been given many different commands which don't even work.
such as "chmod" - i don't know what this does
or even "+777 chmod" - still don't know what it does
or "apt-get install gawk" - comes up with    "cannot find gawk"

i follow the matlab instructions as on the mathworks website    [www.mathworks.com/matlabcentral](www.mathworks.com/matlabcentral)   but the command that tells you to edit "/etc/ftsab" does not allow me to because i do not have permissions.

if you could give me a step-by-step guide on how to install matlab on kubuntu that would be appreciated.
if not, then any suggestions would be greatly appreciated

thanx for your time in reading this problem of mine

---

### Post by ramjet_1953 on 2007-06-09
To modify any file not in your own directory requires root privileges.

For good reasons, too. This way you are prompted to enter your password as modifying system files can do bad things.

so the command you would need is:

[COLOR="Red"]sudo gedit /xxxx/xxxx[/COLOR]

You can then edit this file and save it to your heart's content.

Regards,
Roger :cool:

---

