---
title: "Running programs"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by strahil on 2005-12-03
I installed a few programs(like kweather) with synaptic, but there is no icon for me to open them. could it be linked with the fact that the root terminal doesnt allow me to do sudo commands(permission denied). Any help appreciated.

---

### Post by bluefrog on 2005-12-03
if you can use synaptic then u should be able to sudo. look in synpatic what files were installed by kweather and look for the "executable"
apps>systemtools>menueditor to add a menu..

---

### Post by aysiu on 2005-12-03
Try going to KMenu > Run Command and typing ```
kweather
```

---

### Post by IdolizingStewie on 2005-12-03
The root terminal won't let you use sudo commands because it's redundant. Sudo allows you to run a command as root from a regular terminal. You don't need it in a root terminal.

---

