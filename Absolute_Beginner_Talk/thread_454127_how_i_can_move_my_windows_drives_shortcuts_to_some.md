---
title: "how i can move my windows drives shortcuts to somewhere else?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-05-25
Hi
Thank you for reading my post
Is there any way to remove windows drive shortcuts to somewhere else from my desktop?

for example something like "My computer" or what was present in suse under name of sysinfo:// in its explorer ?


Thanks

---

### Post by REDISISTone.nl on 2007-05-25
> **legolas_w said:**
> Hi
Thank you for reading my post
Is there any way to remove windows drive shortcuts to somewhere else from my desktop?

for example something like "My computer" or what was present in suse under name of sysinfo:// in its explorer ?


Thanks

I don&#8217;t really understand what's your point right now, but if you mean that your windows partition is on your desktop and you want to remove it, just select it and press delete. its just the shortcut you&#8217;re removing so don&#8217;t panic!! it's still available in your file browser.

if this was not what you ment, be more specific please!

---

### Post by legolas_w on 2007-05-25
Thank you for hint.
I want those link to not to be placed in my desktop and instead they could be somewhere else.
I dont want my desktop to be filled with them.

Thanks

---

### Post by Ventrue on 2007-05-25
You can remove all removable media icons from Desktop. Run gconf-editor -> apps->nautilus->desktop->then uncheck volumes_visible :D And now, you have all removable media icons only in "Places" menu :)

---

### Post by Znupi on 2007-05-25
And if you want a "My Computer" icon on your desktop, create a launcher with this command:
```

nautilus computer:///

```
Should work just fine :)

---

