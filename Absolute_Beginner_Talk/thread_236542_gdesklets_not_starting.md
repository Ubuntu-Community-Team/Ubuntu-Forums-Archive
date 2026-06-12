---
title: "gdesklets not starting"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by toykilla on 2006-08-14
I installed gdesklets and everything seemed to work fine. Loaded a few small desklets. Later after I rebooted the desklets would not show up and the gdesklets shell will not load (see attached images)

I uninstalled and reinstalled with the package manager but the same thing is happening.

---

### Post by wjp.reg on 2006-08-14
Have you tried just typing 'gdesklets' into to the terminal?

If that works, maybe try entering gdesklets in the startup sessions under System | Preferences | sessions.

Just enter 'gdesklets' without the shell parameter.

---

### Post by toykilla on 2006-08-14
typing that into the terminal yields:

```

Starting gdesklets-daemon....

```

it just hangs

---

### Post by ljpm on 2007-02-16
I'm having the same problem?  Has anyone solved this yet.

I also uninstalled and reinstalled. Running Edgy.

---

### Post by skennedy1217 on 2007-03-22
I am having the exact same problem.

---

### Post by dracomordag on 2007-03-22
same problem here, too

---

### Post by Damaniel on 2007-03-22
I had the same problem as well.  To fix it, I ended up deleting the entire contents of the '.gdesklets' subdirectory of my home directory ('rm -rf ~/.gdesklets/*').  Of course, this made me lose all of the settings for the existing desklets (all 3 of them) that I had configured, but at least I could start the program up and reconfigure them again.

---

### Post by igknighted on 2007-03-22
> **dracomordag said:**
> same problem here, too

"With a horse made of crystal he patrolled the land..."

I think that if you save the config files for the desklets elsewhere, delete the .gdesklets folder, then run gdesklets you can then add the config files back to the new .gdesklets folder... not sure 100% tho

---

