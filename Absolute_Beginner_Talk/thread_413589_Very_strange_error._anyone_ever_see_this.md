---
title: "Very strange error. anyone ever see this?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by lamalex on 2007-04-19
This is pretty much trivial, but I was cleaning off a disk and got this
> 
rm: cannot remove directory. "file exists."

I'm in as root doing rmdir, rm -d, rm -r, rm -rf, rm -df and get the same error every time.

---

### Post by dasunst3r on 2007-04-19
When you are deleting a folder using the *rm* command, the folder must be empty.  If you want to delete a folder, you need to issue the command *rm -rf {directory}*.  The 'r' part of the parameter means "recursive," and it will delete everything inside the folder, *then* the folder itself.

---

### Post by Skrynesaver on 2007-04-19
Could you do a 
```
rm --version
```
i did a ```
strings $(which rm)
``` and got no mention of the message you report (I hadn't seen it before so I was curious as to what else I might yet encounter ;)

---

### Post by lamalex on 2007-04-21
> **dasunst3r said:**
> When you are deleting a folder using the *rm* command, the folder must be empty.  If you want to delete a folder, you need to issue the command *rm -rf {directory}*.  The 'r' part of the parameter means "recursive," and it will delete everything inside the folder, *then* the folder itself.

.. i know that, Did you read the post? I said I had tried almost every variation of rm and rmdir including -f. also, the folder was empty. we had done multiple ls -la inside the directory with nothing coming back

---

