---
title: "help with this sed statement...learning.."
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2008-03-18
Hi,

i want to change:

/cgi-bin/ubb_cgi/forumdisplay.cgi?action=topics&forum=Levell+One&number=5

to:

../../Fourm Menu/forumdisplay.cgi_action=topics&forum=Level+One&number=1

sed -i 's/\/cgi-bin\/ubb_cgi\/forumdisplay\.cgi\?action=topics&forum=Level+One&number=5\.\.\/\.\.\/forumdisplay\.cgi_action=topics&forum=Level+One&number=1/g' /home/firebox/Forum5/HTML*.html

what am i doing wrong here?

thanks !!!

---

### Post by finferflu on 2008-03-18
First of all I'd suggest to use another separator in place of / as it will get very confusing, just use # for example. So:

```
sed -e 's#/cgi-bin/ubb_cgi/forumdisplay.cgi?action=topics&forum=L evell+One&number=5#../../Fourm Menu/forumdisplay.cgi_action=topics&forum=Level+On e&number=1#'
```

---

