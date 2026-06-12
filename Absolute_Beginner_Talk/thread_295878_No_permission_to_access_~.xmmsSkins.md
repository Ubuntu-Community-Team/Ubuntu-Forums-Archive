---
title: "No permission to access ~/.xmms/Skins?"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by TangerineSkyy on 2006-11-08
I'm trying to install an xmms skin but it says I don't have permission. I just learned how to log in as root, but I'd rather not. How can I move or extract a skin folder to  ~/.xmms/Skins when clicking and dragging just won't work?

I'm thinking the answer is in the terminal, but I'm not sure what command to use.

Thanks

-a recent convert.

---

### Post by bodhi.zazen on 2006-11-08
What are the permissions on ~/.xmms/skins ?

```
ls -l ~/.xmms
```

At any rate, the commnad you want is:

[mv <xmms_skin_location> ~/.xmms/Skins[/code]

---

### Post by TangerineSkyy on 2006-11-08
That didnt work, so I just used sudo and it worked... I didnt get any confirmation or any acknowledgement that it got moved (aside from checkign the ~/.xmms/Skins and seeing my new skin there)... Is there an option I can use to have it say something when it moves?


EDIT: Forgot to say thanks!

---

### Post by bodhi.zazen on 2006-11-08
The "Linux way" is *no output if a command is successful*.

Your permissions may be off with either ~/.xmms or ~/.xmms/Skins.

Not sure if it matters to you, but you can change them with chown and chmod.

---

