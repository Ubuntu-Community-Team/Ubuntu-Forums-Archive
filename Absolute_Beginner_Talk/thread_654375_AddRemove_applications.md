---
title: "Add/Remove applications"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by path_finder on 2007-12-31
Hi everyone,
I connect my laptop to the internet from a internet cafe. Problem is Mozilla recognize that I am in the internet. But when I try to install applications from add/remove applications interface it dosent work. If have configured the ip address, dns.... . where is the problem?

---

### Post by LaRoza on 2007-12-31
Run:

```

sudo apt-get update

```

---

### Post by jualin on 2007-12-31
Maybe you do not have the online repositories enabled. If you use synaptic you could enable them in Settings and Repositories. You need to enable universe repositories. Hope this helps.

---

