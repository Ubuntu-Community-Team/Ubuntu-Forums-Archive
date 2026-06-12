---
title: "Post-Installation problems"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Arun007 on 2008-02-15
I have installed Ubuntu in my Pc. I don't have internet connection in my pc. I have downloaded it manually from cyber-cafe. When i tried to install the codecs. It gives me the error saying"Dependency not satisfiable". Please help

---

### Post by Joeb454 on 2008-02-15
You need to be connected to the internet for it to download the codecs. Is there no possibility of your PC being connected to the internet?

---

### Post by Arun007 on 2008-02-15
Nopes no possibility, I heard of Ubuntu Plus. Can i do it through Ubuntu plus

---

### Post by hyper_ch on 2008-02-15
well, certain programs / libraries depend on other stuff... those are dependencies. You need to download all the dependencies to install the codecs.

---

### Post by Joeb454 on 2008-02-15
You might be able to download the DVD edition of Ubuntu (possibly get somebody else to do it for you?) And then install from that, it contains a lot of the extra things people want on the DVD.

Failling that I'd [check out Linux Mint]("http://linuxmint.com/"), it's based on Ubuntu and comes with a lot of things already preinstalled, like Flash/Java etc.

---

### Post by hyper_ch on 2008-02-15
synaptic has an option (I think) that shows all dependendencies. So you might just use that list to download what you need.

---

### Post by Arun007 on 2008-02-15
Ok. My friend has Ubuntu DVD. Will i be able to install codecs from it.

---

### Post by Joeb454 on 2008-02-15
I think you should be able to. You may have to edit your software sources. But we'll come to that later if we need to :)

---

### Post by Arun007 on 2008-02-15
After i inserted the DVD disc. It showed two options start package manager and another which i dont remember. I started the package manager. Don't know what to do next.

---

### Post by Joeb454 on 2008-02-15
Try and install the codecs you want? do a search for what you want to install, and then try and install it. If it's somewhere on the DVD it'll install it for you :)

---

### Post by Arun007 on 2008-02-15
Is there any way ubuntu can install it automatically

---

### Post by hyper_ch on 2008-02-15
define "automatically"

---

### Post by kpkeerthi on 2008-02-15
> **Arun007 said:**
> After i inserted the DVD disc. It showed two options start package manager and another which i dont remember. I started the package manager. Don't know what to do next.

From the package manager (synaptic), search for **ubuntu-restricted-extras** and install it.

---

### Post by Arun007 on 2008-02-15
hyper_ch. Previously it used to ask Install automatically. But it doesnt ask now

---

### Post by Arun007 on 2008-02-15
@Keerthi. When i do that. It starts downloading from net

---

### Post by kpkeerthi on 2008-02-18
> **Arun007 said:**
> @Keerthi. When i do that. It starts downloading from net

Can you try adding the DVD as  a repository from Settings > Repositories in Synaptic or System -> Admin -> Software Sources ?

---

