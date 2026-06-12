---
title: "Virturalbox Autostart?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Dissident85 on 2008-02-15
Is it possible to get a guest os to start up when i log in?

---

### Post by kpkeerthi on 2008-02-15
**Method - 1: **
To list the VMs registered with VirtualBox, open a terminal and run
```

VBoxManage list vms

```

To start a VM from command line
```

VBoxManage startvm "<vm-name-from-the-above-command>"

```
**Example:**
```

VBoxManage startvm "Gentoo"

```
Test it working and then add the above command to System -> Preference -> Session

**Method - 2 (Using Remote Desktop Protocol (RDP)):**

1. Start the Vm with Vbox VRDP protocol
```

VBoxManage startvm <vmname> **-type vrdp**

```

2. Connect to the VM
```

rdesktop -a 16 localhost

```

*-a 16 option requests a color depth of 16 bits per pixel, which is recommended. You should set the color depth of your **guest** operating system to the same value. Look for DefaultDepth in /etc/X11/xorg.conf and change it to 16

---

### Post by HappyFeet on 2008-02-15
:-k

---

### Post by amingv on 2008-02-15
If you want it to start in fullscreen mode always, you can use this too:

```
VBoxSDL -fullscreen -vm 'nameOfVirtualMachine'
```

---

### Post by Dissident85 on 2008-02-15
Thanks kpkeerthi that worked :)

---

### Post by Dissident85 on 2008-02-15
> **amingv said:**
> If you want it to start in fullscreen mode always, you can use this too:

```
VBoxSDL -fullscreen -vm 'nameOfVirtualMachine'
```

is that the same as seamless mode?

---

### Post by amingv on 2008-02-15
> **Dissident85 said:**
> is that the same as seamless mode?

No, I didn't find a way to go directly into seamless mode, but it's not hard to press Host+L after that.

---

