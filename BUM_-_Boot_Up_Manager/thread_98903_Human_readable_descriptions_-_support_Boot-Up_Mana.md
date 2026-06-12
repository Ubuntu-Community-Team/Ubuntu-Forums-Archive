---
title: "Human readable descriptions - support Boot-Up Manager"
date: 2005-12-04
forum: BUM - Boot Up Manager
---

### Post by saltydog on 2005-12-04
Almost all the services started with init scripts in runlevels 2-3-4-5 and rcS.d don't have a standard, "human readable" description of their main behaviour. Very often the package description for these services is very cryptic and the common user is quite disorientated and doesn't understand the meaning. Boot-Up Manager (BUM) will use a special list to display the package description in its main view window.

If in the "Running" column of BUM main window list you have displayed a question mark (?) it means that BUM doesn't have a nicer description for the service and so it is showing the apt-cache description. The internal "human-text" list is under a constant updating process. To contribute to this list, please feel free to update **[this wiki-web page]("http://wiki.ubuntu.com/InitScriptHumanDescriptions")**.

---

