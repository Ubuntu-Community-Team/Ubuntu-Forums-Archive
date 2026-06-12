---
title: "Why Ubunut is complaining on these files?"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by HuBaghdadi on 2008-02-10
Hi.
I have some files that I copied from Windows XP box, like HTML files and text files.
When trying to open them on Ubuntu, a dialog pops up indicating that the file is execute with options buttons (Display, Cancel, Run in terminal)
Why?
Thanks.

---

### Post by LaRoza on 2008-02-10
That is ok, just click "display" to view them.

---

### Post by PeterJS on 2008-02-10
They picked up an execute flag some where in life, probably on the fat32 or ntfs drive you used to transport them. So to get the error to go away, find the files in the file browser, select them, right click and select properties, on the permissions tab uncheck the execute box down at the bottom.

---

### Post by HuBaghdadi on 2008-02-10
Yes but in general, why it is complaining?

---

### Post by PeterJS on 2008-02-10
> **HuBaghdadi said:**
> Yes but in general, why it is complaining?

Because gnome doesn't know what to do with them. They have the execute flag (and a text mime type), so as far as the system knows they're scripts, rather than gnome saying when you open a script you always want to run the script, or always want to edit the script, gnome instead asks every time.

---

### Post by aysiu on 2008-02-10
It's not *complaining* about the files; it's *prompting* you for what to do with the files.

You'll get prompted in that way for any executable text file, as Gnome wants to give you the option to execute it, execute it in the terminal, or view the text. That's the default behavior, anyway.

If it bothers you that much, you can change the behavior in Nautilus by going to **Edit > Preferences > Behavior > Executable Text Files > View executable text files when they are opened**

Or, as others have mentioned, you can just make the text files non-executable.

---

