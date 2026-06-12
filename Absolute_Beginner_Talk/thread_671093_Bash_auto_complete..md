---
title: "Bash auto complete."
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by skeiths on 2008-01-18
Hi,
I just installed ubuntu server. I then updated my apt-get.
I then done a apt-get install ee
As you may know, ee is a text editor, my preferred one.
my problem is with the tab (auto-complete)

if i do "vi" I can tab filenames or directories.
with "ee" I can only tab directories, it wont recognise filenames for auto-completion.

I would like to know how to fix/tweak this so ee auto-complete finds files.

Thanks,
Keith

---

### Post by skeiths on 2008-01-18
I have found more info
bash command "complete" is for more intelligent completion.
complete | grep " ee" returns this
complete -o filenames -F _filedir_xspec ee

I think its this line that i need to tweak, but I dont know what it means yet.
Thanks in advance for any help.

---

### Post by SOULRiDER on 2008-01-18
Can you do complete | grep " vi" and modify the one for ee to look like vi's ?

---

### Post by skeiths on 2008-01-18
complete | grep " vi" ; complete | grep " ee" returns
complete -o filenames -F _filedir_xspec view
complete -o filenames -F _filedir_xspec vi
complete -o filenames -F _filedir_xspec vim
complete -o filenames -F _filedir_xspec ee

so, now i am more puzzled.

---

