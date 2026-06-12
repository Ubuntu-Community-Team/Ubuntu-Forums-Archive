---
title: "iBook 800 MHz G4 + Ubuntu 10.04 + Compiz?"
date: 2011-02-20
forum: Apple Hardware Users
---

### Post by ownaginatious on 2011-02-20
So I recently decided to install Ubuntu 10.04 on my old iBook G4, and so far it's working quite well.

The only other feature I would like to enable is Compiz, which the computer doesn't allow me to do.

When I run, 'compiz' in the terminal, I get the following output:

```

compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

```

Anyone know what I can do about this?

The video processor this computer has is an ATI Radeon 9200... ancient, I know ;)

Thanks!

---

### Post by ownaginatious on 2011-02-20
Never mind, I figured it out.

Turns out the solution was to add a flag to the yaboot.conf.

For anyone looking for this solution in the future, the flag I added was 'radeon.modeset=0' like so:

```

append="quiet splash radeon.modeset=0"

```

Then I ran,

```

sudo ybin

```

---

