---
title: "[SOLVED] How to suppress &amp;quot;Permission Denied&amp;quot; messages when using find"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-10-18
I remember there was an option for suppressing the messages when using find, but I couldn't find any relevant option on the man page.

---

### Post by ronald.higgins on 2007-10-18
You can use the 2>/dev/null to send any errors to /dev/null eg. "find / -name 'program.c' 2>/dev/null"

rH

---

### Post by hyper_ch on 2007-10-18
run find as sudo.

---

### Post by ronald.higgins on 2007-10-18
Although sudo doesn't help if you dont have access to root.

---

### Post by hyper_ch on 2007-10-18
sudo gives you access to root ;)

---

### Post by ronald.higgins on 2007-10-18
You're presuming that he is the Admin of the box and has access to use the root account.
Not all users are the admin of the box.

If he is a normal user your solution doesnt help, and the question was how to
"suppress the permission denied error" no ? 

;)

---

### Post by hyper_ch on 2007-10-18
ronald:

There is no hint is he not admin of that box ;) hence I believe it his box... otherwise he should have told ;)

And running the find command with the sudo prefix it will suppress the permission denied error in a way, that there will be none ;)

---

### Post by ronald.higgins on 2007-10-18
I think we're arguing about semantics now,

none the less .. i think we've provided a solution to both scenarios ;)

---

### Post by tkharris on 2007-10-18
If he runs it with sudo ( assuming he has it ), and doesn't need it, he's wasting processor time.

Assuming he doesn't have it, and runs it with sudo it won't supress the errors, it'll prompt him for a password tell him to go f himseld, email the admin and his command will never be run.  ;)

Also if you're planning to run find on /, you should use locate instead.  ^.^

---

### Post by AncientPC on 2007-10-18
Thanks guys.  Yes I do have root access but using sudo to suppress the errors isn't what I was looking for.

Ronald: That works great, what's "2>/dev/null" doing anyhow?

tkharris: What's the difference between locate and find?  I noticed locate has the -q option to suppress error messages . . .

---

