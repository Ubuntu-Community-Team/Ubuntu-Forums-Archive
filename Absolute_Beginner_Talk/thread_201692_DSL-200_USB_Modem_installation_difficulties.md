---
title: "DSL-200 USB Modem installation difficulties"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by adam s on 2006-06-22
Hi,

I am trying to get my USB DSL-200 modem working from Ubuntu.

I have tried to install the Debithe gdebi package installeran (Ecidsl driver) from the Flashtex site, but I get  a 'Dependency is not satisfiable : PPPoE' error when I attempt to open the package with the gdebi package installer.

Does anyone know how to get round this?


Thanks in advance,

Adam.

NB. I have seen a post elsewhere on this forum telling you to download the files from the designer's site - but I cannot find this driver anywhere else but on the flashtex site.

---

### Post by renzokuken on 2006-06-22
when it says "dependency not satisfied" it means that there is a package not installed on your system that is needed by the driver. in this case it is a PPPoE package.

the drivers homepage should list dependencies, if not just search synaptic for PPPoE and install anything that looks close there

---

