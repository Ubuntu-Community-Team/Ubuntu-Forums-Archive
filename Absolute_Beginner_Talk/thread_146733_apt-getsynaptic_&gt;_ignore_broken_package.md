---
title: "apt-get/synaptic &gt; ignore broken package?"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by mackinax on 2006-03-18
Is there a simple`ish way I can I make apt-get/synaptic ignore a "broken" package? 

I searched and read many threads about this topic, but only one seemed to have a real solution. It said something about creating a dummy package. But I'm not sure if I can do that in my situation, because the broken packages arent truly missing, they're just older versions than are necessary.

edit: typo

---

### Post by aysiu on 2006-03-18
From the apt-get man page: > -f, --fix-broken
              Fix;  attempt  to  correct  a system with broken dependencies in
              place. This option, when used with install/remove, can omit  any
              packages  to permit APT to deduce a likely solution. Any Package
              that are specified must completely correct the problem. The  op&#8208;
              tion is sometimes necessary when running APT for the first time;
              APT itself does not allow broken package dependencies  to  exist
              on a system. It is possible that a system’s dependency structure
              can be so corrupt as to require manual intervention (which  usu&#8208;
              ally  means  using dselect(8) or dpkg --remove to eliminate some
              of the offending packages). Use of this option together with  -m
              may  produce  an  error  in some situations. Configuration Item:
              APT::Get::Fix-Broken.

       -m, --ignore-missing, --fix-missing
              Ignore missing packages; If packages cannot be retrieved or fail
              the  integrity  check after retrieval (corrupted package files),
              hold back those packages and handle the result. Use of this  op&#8208;
              tion  together  with -f may produce an error in some situations.
              If a package is selected for installation (particularly if it is
              mentioned  on  the  command line) and it could not be downloaded
              then  it  will  be  silently  held  back.  Configuration   Item:
              APT::Get::Fix-Missing.
 I believe you'd do something like ```
sudo apt-get -f install
```

---

### Post by mackinax on 2006-03-18
I should have been more specific. I'm sorry.

**-f** or **-m** will not work in this case, as far as I understand, because the necessary package versions are not available in the repositories. (including uni/multiverse or backports)

I was hoping to quit while I was ahead, since the updated software is working - in spite of having missing dependencies. But I suppose I will have to either revert back to a safe place, or continue pressing my luck by manually installing unsupported pkgs. 

Thanks for the help anyhow!

---

### Post by aysiu on 2006-03-18
Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

