---
title: "Can I install an Edgy package on Dapper?"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by jamadagni on 2006-08-12
There are some packages available for Edgy only, such as [Qt 4.2 Designer]("http://packages.ubuntu.com/edgy/devel/qt4-designer-kdecopy"). I need to use this on Dapper. Is it possible?

Or do I have to recompile from source or something? (I know rpmbuild on RPM-based systems but what is it for DEB?)

---

### Post by jordilin on 2006-08-12
It's quite dangerous installing Edgy soft to Dapper. You'll end up with tons of dependencies issues. I would enable the backports repository to see if it was there, or build from source. Or simply switch to Edgy, sth I don't recommend because things get broken very easily as it's in a development stage.

---

