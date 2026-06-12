---
title: "Gnote 0.7.3 does not start"
date: 2011-04-10
forum: Any Other OS
---

### Post by lduperval on 2011-04-10
Hi,

I recently updated the version of Gnote to 0.7.3 and since then, it has stopped working with the following error message:

```

gnote: symbol lookup error: gnote: undefined symbol: _ZN4DBus13BusDispatcherC1Ev

```

I tried reinstalling and have the same error. I tried building it manually but I get problems when trying to link to Boost:

```

configure: error: Could not find the flags to link with Boost filesystem

```

So now I'm stuck and I have a lot of information stored with gnote. I tried to go back to 0.7.2 (which was the previously installed version) but synaptic says it only has 0.6.2 available.

Does anyone have the same issue? If so, how have you resolved it? 

Thanks,

L

---

### Post by stinkeye on 2011-04-10
I just updated gnote to 0.7.3 through the stable ppa.
When installing it also updated a package called **libdbus-c++-1-0**
to version **0~20110310-1~ppamaverick1**

How did you update to version 0.7.3 ?
Are you still using Karmic?

[**_[COLOR="DarkRed"]Gnote stable ppa[/COLOR]_**]("https://launchpad.net/~gnote/+archive/ppa")

---

### Post by lduperval on 2011-04-10
No I'm on Lucid (Well, Linux Mint 9, which is based on Lucid). It also updated libdbus to the same version as yours.

Since I absolutely had to fix this, I ended up compiling from source (which is another story) and logged a bug report on Launchpad.

I'll have to wait for the next update before trying to re-install.

L

---

