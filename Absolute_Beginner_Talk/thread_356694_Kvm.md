---
title: "Kvm"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by gaby PR on 2007-02-08
Is KVM Virtualization program available in ubuntu repositories?

If it.

How I install it?

Thanks

---

### Post by chuckyp on 2007-02-09
Its available in fiesty repos.  If it isn't in whatever version you are running you could always download the source and compile yourself.  To see if something is available you can search synaptic or apt-cache search kvm   would display if its in the repos you have enabled.

---

### Post by incubus on 2007-02-12
If you're running Feisty, all you need to do is
```

$ sudo apt-get install kvm

```

Check this out for instructions
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

But again, this is in Feisty, not Dapper or Edgy.  KVM requires the new kernel to run and of course a VT enabled processor.

incubus

---

