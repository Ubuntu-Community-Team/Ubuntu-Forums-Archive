---
title: "Preventing a folder from being deleted"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by argie on 2007-11-02
I accidentally deleted a folder a long time ago and didn't even notice it. I was just looking for it and noticed it just now. What I'd like to know is, how do I prevent a folder from being deleted *without preventing me from adding files to it*. I tried to do that by creating a folder to which I had write permissions but made the files inside such that I wasn't allowed to write to them but I could still accidentally delete the folder.

Is there a way that I can do this?

---

### Post by jw5801 on 2007-11-02
> **argie said:**
> I accidentally deleted a folder a long time ago and didn't even notice it. I was just looking for it and noticed it just now. What I'd like to know is, how do I prevent a folder from being deleted *without preventing me from adding files to it*. I tried to do that by creating a folder to which I had write permissions but made the files inside such that I wasn't allowed to write to them but I could still accidentally delete the folder.

Is there a way that I can do this?

Hmm... not that I'm aware of. How did you accidentally delete a folder? And if you just deleted it via nautilus, then it should be in the trash still (~/.Trash).

---

### Post by john lejeune on 2007-11-02
Argie, is ```
rm -rdi ~/Desktop/myTestDir/
``` yours command line solution?

---

### Post by Inxsible on 2007-11-02
I don't think you can do that. Deleting is actually in a sense "writing" to that particular reference location with something else(junk maybe).

so you cannot have write permission on the folder and not be able to delete it.

your best option is to assign root as the owner, so that you have to provide the password to write into or delete anything from it. That will atleast tell you you are doing something and hopefully make you look closer to what you are trying to delete :)

---

### Post by argie on 2007-11-02
> **jw5801 said:**
> Hmm... not that I'm aware of. How did you accidentally delete a folder? And if you just deleted it via nautilus, then it should be in the trash still (~/.Trash).

I was incredibly foolish, I didn't notice at the time. My touchpad was enabled to accept taps, you see, so I accidentally sent the file to Trash and didn't notice. Then I later emptied out the Trash without looking :D

> **john lejeune said:**
> Argie, is ```
rm -rdi ~/Desktop/myTestDir/
``` yours command line solution?

Hey, neat, thanks. I'll use that -i thing as an alias. But I deleted this from Nautilus.

> **Inxsible said:**
> I don't think you can do that. Deleting is actually in a sense "writing" to that particular reference location with something else(junk maybe).

so you cannot have write permission on the folder and not be able to delete it.

your best option is to assign root as the owner, so that you have to provide the password to write into or delete anything from it. That will atleast tell you you are doing something and hopefully make you look closer to what you are trying to delete :)

That's what I thought. Deleting is 'writing', after a fashion. I suppose I'll just have to live with making that folder read only except when I'm copying stuff to it. So be it then. Thanks everybody.

EDIT: It just struck me. Is there a setting for making Nautilus do a "Do you want to delete this?" prompt instead of just moving to Trash?

---

