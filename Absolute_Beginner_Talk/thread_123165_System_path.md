---
title: "System path?"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by Jimmey on 2006-01-29
"Make sure a symbolic link to the realplay script is in your PATH."
How'd I do that?

---

### Post by christhemonkey on 2006-01-29
export PATH=$PATH:/wherever/your/file/is/

---

### Post by Jimmey on 2006-01-29
I've already tried, and still Firefox says:
> Could not find appropriate hxplay or realplay in the system path to use as an embedded player
What should I do? The .bin's at 
> /home/james/RealPlayer
And so I typed 
> export PATH=$PATH:/home/james/RealPlayer
But still no joy :(:(

---

### Post by christhemonkey on 2006-01-29
sorry make sure you put " "'s around the directory, so:

export PATH="$PATH:/home/james/RealPlayer"

---

### Post by Jimmey on 2006-01-29
I'm still getting that error message, even after I've run the post install script?

---

### Post by christhemonkey on 2006-01-29
type 
echo $PATH
just to check...(should be the last item)

---

