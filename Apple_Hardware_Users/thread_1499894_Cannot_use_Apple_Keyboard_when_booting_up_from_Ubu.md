---
title: "Cannot use Apple Keyboard when booting up from Ubuntu 10.04 CD"
date: 2010-06-02
forum: Apple Hardware Users
---

### Post by sushiboy on 2010-06-02
Hello everyone!

I've tried Ubuntu awhile ago. I popped the CD then restarted my Mac. Upon restarting I usually pressed the C key. The system boots to the Ubuntu CD but when I get to the language selection thing, I cannot use my keyboard. I had to snag my PC's keyboard from the other room to make it pass through the said window.

Is it normal? I selected the "Try Ubuntu" first to get my feet wet.

---

### Post by sha.goyjo on 2010-06-02
Which apple keyboard is this? Is it one of the bluetooth ones? I don't think that the bluetooth system is initialized before the CD boots, so you can't use it that early. You should be able to use it at startup once the system boots to the login screen, but I don't think there is any way of navigating the pre-boot with a bluetooth keyboard. Don't hold me to it, but as far as I know, there isn't.

---

### Post by sushiboy on 2010-06-02
It's the wired keyboard, the earlier batch along with the now defunct Mighty Mouse wired. Pressing it doesn't get me anywhere, as well as pressing the mouse.

---

### Post by sha.goyjo on 2010-06-02
That's really unusual.....

Oh duh. The keyboard contains a hub, which isn't being enumerated before the kernel is loaded. Since the keyboard is probaby technically on the other side of the hub (see below) it isn't getting recognized before the kernel is booted

Computer----hub in keyboard----keyboard itself
[COLOR="Silver"].............................[/COLOR]|--- usb port
[COLOR="Silver"].............................[/COLOR]|--- usb port

That's just a guess though. As I said, this shouldn't be a problem at any point in the process after the kernel is booted. But before it is booted the keyboard may be non functional.

Again, I'm not sure. Can somebody with better knowledge of the internals of the keyboard comment?

---

### Post by sushiboy on 2010-06-02
Anyone else having this error?

---

### Post by redxine on 2010-07-19
Not with the wired keyboard, or wireless for that matter. I just booted fedora 11 with no problems with the keyboard or mouse (except scrolling). This is a relatively new Mac though.

---

### Post by DoubleClicker on 2010-07-19
> **sushiboy said:**
> Anyone else having this error?

That was not my experience, my keyboard was recognize right away. However, it is possible that there is something about your keyboard, which is different than mine, even if they are the same model.

---

