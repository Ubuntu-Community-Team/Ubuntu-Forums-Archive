---
title: "[SOLVED] problem reload synaptic package manager"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by rahulsharma on 2008-01-20
hey all the problem is when i hit the reload button it downloads couple of files but then gives me an error 
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9

i thought it may be because the US server would be under maintenance but this problem is for past couple of days.....does anyone have any idea about it....

---

### Post by smartboyathome on 2008-01-20
Are you using an external repo? If so, then that is why you are getting that error. Disable the repo to get synaptic working again.

---

### Post by rahulsharma on 2008-01-23
do you mean multiverse by the term external repo....

---

### Post by forestpixie on 2008-01-23
no I guess he's talking about 3rd part ones like tuxfamily - the ubuntu ones aren't 'external' as such

---

### Post by rahulsharma on 2008-01-24
i am not sure where i can see if i have enabled any external repo as i haven't selected software from third party...if you could let me know how to check that whether i have selected it or not..
thanks

---

### Post by rahulsharma on 2008-01-24
oh ok i got that ..they were checked now i can reload the  package manager but one quick questions.
what is the tuxfamily software are used for, if i keep them unchecked how it will effect.

---

### Post by RomeReactor on 2008-01-24
Hi. If you upgraded from Feisty to Gutsy and used Beryl previously, then you need to disable the repository you added; go to 'System->Administration->Synaptic, and once it opens go to 'Settings->Repositories'. There go to the second tab (Third-Party Software) and uncheck the TuxFamily repository there--and any other from Feisty. Then close that window and, still in Synaptic, press the blue 'Reload' button.

EDIT: Too slow. The TuxFamily repository was used in Feisty to add Beryl, among other eyecandy programs; you can safely disable it, since Gutsy now uses Compiz, which is Compiz and Beryl merged back.

---

### Post by rahulsharma on 2008-01-25
thanks a ton for this information but how you guys get to know so much about ubuntu is there any website or some stuff to get so perfect or its just practice and time...anyway thanks for the info i will mark it solved,,,

---

