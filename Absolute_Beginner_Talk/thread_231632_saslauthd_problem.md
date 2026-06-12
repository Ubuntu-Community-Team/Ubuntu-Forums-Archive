---
title: "saslauthd problem"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by rich1231 on 2006-08-07
Hi there,

Im building a server at the moment.. Im likely to bin it and start again once ive learnt a few bits and pieces though.

Im trying to restart saslauthd

The /etc/default/saslauthd file =

# This needs to be uncommented before saslauthd will be run automatically
START=yes

PWDIR="/var/spool/postfix/var/run/saslauthd"

PARAMS="-m ${PWDIR}"

PIDFILE="$[PWDIR}/saslauthd.pid"

# You must specify the authentication mechanisms you wish to use.
# This defaults to "pam" for PAM support, but may also include
# "shadow" or "sasldb", like this:
# MECHANISMS="pam shadow"

MECHANISMS="pam"


but when i try and start saslauthd
I get the following:

richard@plaything:/etc/default$ sudo /etc/init.d/saslauthd start
/etc/default/saslauthd: line 15: unexpected EOF while looking for matching `"'

anyone got a clue what is wrong?#


Regards

Rich

---

### Post by bscbrit on 2006-08-07
Did you cut-and-paste your code or retype it?  It might be worth checking it very closely for a missing "

---

### Post by bscbrit on 2006-08-07
Try putting a CR at the end of the last line.

---

### Post by rich1231 on 2006-08-07
it has 0a in hex on the end of line 15

i edited the file with Gvim

---

### Post by rich1231 on 2006-08-08
anyone else have any ideas?

---

### Post by bscbrit on 2006-08-08
Copy your existing file somewhere safe, say sasauthd.orig, and then retype the entire thing.  Might be a hidden character or something, but other than that I am out of ideas.

---

### Post by rich1231 on 2006-08-09
thanks for the tip, tried it but doesnt work, there isnt even a line 15 in the retyped file, but it still reports the same error.
Is it possible that its mis-reporting where the error is?

---

### Post by bscbrit on 2006-08-09
Are you sure that you are editing the correct file?  From your original post:

PWDIR=/var/spool/postfix/var/run/saslauthd"

The /etc/default/saslauthd file =

I don't know for sure, but should you be editing the /etc/default/ or /var/spool/postfix/var/run/ copy of saslauthd???

Just a thought. :confused:

---

### Post by rich1231 on 2006-08-09
Ill try it when i get home....
if so do i win retard of the week?

---

### Post by bscbrit on 2006-08-09
You're not alone.  Its taken half a dozen posts for us _both_ to get here!

---

### Post by rich1231 on 2006-08-09
right,

i dont think that is it... the /etc/default is the right location for saslauthd it seems, then the parameters within point to the other directory

---

### Post by bscbrit on 2006-08-10
> **rich1231 said:**
> right,

i dont think that is it... the /etc/default is the right location for saslauthd it seems, then the parameters within point to the other directory

Yes, I agree, but in which copy of the file is the computer finding the error?  The error message is suitably vague that perhaps you should check both.

Failing that, try a complete removal of the offending package using Synaptic (use the remove all option to ensure that the config file is also removed) and then re-install.

---

