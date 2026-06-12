---
title: "Beagle misbehaves"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-03-18
Hi group,
Trying to get Beagle to work.
I've tried doing this,

sudo aptitude install beagle deskbar-applet


then beagled



Nothing.

I've also tried installing it through Automatix.

My book says that I should now right click on a panel and add the applet to the panel, but it doesn't show in my panel.

What am I doing wrong?
Thanks,
Phil

---

### Post by AtrejuT on 2007-03-18
well, what do you mean by nothing? Does it install or does it give some error message? If so, what error message does it give?

atreju

---

### Post by groeswenphil on 2007-03-18
Tried again and this time found a little search icon in the shape of a magnifying lens.
I expected to see a dog with long ears.

Does this mean it's working? It appears to be doing what I want it to do.
All the best,
Phil

---

### Post by AtrejuT on 2007-03-18
it is a lens for me, but then I'm on feisty.
But I think that's what you want.

---

### Post by groeswenphil on 2007-03-18
Then I get this


$ beagled
Beagle Daemon exited with errors.  See ~/.beagle/Log/current-Beagle for more details.


Phil

---

### Post by AtrejuT on 2007-03-18
can you tell me what the content of that log-file is?
```

tail ~/.beagle/Log/current-Beagle

```

---

### Post by joncheyne on 2007-03-18
> **groeswenphil said:**
> Tried again and this time found a little search icon in the shape of a magnifying lens.
I expected to see a dog with long ears.

Does this mean it's working? It appears to be doing what I want it to do.
All the best,
Phil
The magnifying glass is right - this shows you have the latest version - click once on it to open a search dialog. No need to run beagled any further ..

What happens if you click on the glass and try a search?

---

### Post by groeswenphil on 2007-03-18
I get a search page up.
It says,
Name contains,
Look in folder
and select more options.

---

### Post by groeswenphil on 2007-03-18
tail ~/.beagle/Log/current-Beagle

How do I find this file? I tried the search, but it couldn't find it.
Phil

---

### Post by groeswenphil on 2007-03-18
:guitar: 

Thanks..............everything working now.

I had it in my mind that I was needing to add a beagle to the task bar.
I should have been looking for DESKBAR

You know..............everybody is just great here, freely giving their time to help sort out idiots like me.
Big thanks everybody.
Phil

---

