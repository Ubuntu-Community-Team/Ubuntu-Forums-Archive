---
title: "runnunig a sh file"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-07-19
I must run a file called results with the comand sh resuls.

Shuold the results file have an .sh extension and should i make it an exe 
ie chmod x+?

the results file is 16k and is amend permissions
it looks like this:

# /var/spool/news/archive:0: mode 775, should be 755
chmod 755 /var/spool/news/archive
# /var/spool/news/incoming/bad:0: mode 775, should be 755
chmod 755 /var/spool/news/incoming/bad
# /var/spool/news/outgoing:0: mode 775, should be 755
chmod 755 /var/spool/news/outgoing
# /usr/lib/news/bin/control:0: owned by root, should be news
chown news /usr/lib/news/bin/control
# /usr/lib/news/bin/control:0: in group root, should be news
chgrp news /usr/lib/news/bin/control
# /usr/lib/news/bin:0: owned by root, should be news
chown news /usr/lib/news/bin
# /usr/lib/news/bin:0: in group root, should be news 


lex1

---

### Post by OpsVentus on 2006-07-19
.sh extension is not needed I think, but you need to set the x bit. Then you can run it.

---

### Post by lex1 on 2006-07-19
am i correct in thinking that the # in the results file should be removed?

lex1

---

### Post by OpsVentus on 2006-07-19
Hi Lex,
No you can leave them there. Every line starting with # will be 
considerd comment and are not executed.

Cheers,
Bart.

---

### Post by lex1 on 2006-07-19
run as root i expext?

lex1

---

### Post by OpsVentus on 2006-07-19
If your going to modify stuff not allowed by the user. (For example changing owner from root) Then you will have to run it as root.

Cheers,
Bart.

---

