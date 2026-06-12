---
title: "Help with permission problem"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by _mOrgoth_ on 2006-10-15
Hi!
Ok... I have fresh Ubuntu 6.06 installation. Comp is using for Counter strike source dedicated server. In "admin" directori i created "srcds" directori and there instaled Steam dedicated server for linux. Using text editor i created script server.cfg and temporaly I placed it on desktop. Now I must copy it in admin/srcds/cstrike/cfg directori. I try with krusader but it tells that i dont have the permission to access??? When I use file browser it opens admin/srcds, but when I try open cstrike (admin/srcds/cstrike) It say: The folder contents could not be displayed: You do not have permissions necessary to viev the contents of "cstrike". Before ubuntu I used xubuntu, kubuntu and I didnt have this problem. Also, it works fine when I use root-File Browser(gksudo nautilus). Momently I am ](*,) !!!!!!!! Please help!

p.s. sorry for my poor english.

---

### Post by NeoLithium on 2006-10-15
Type this,and you should be ok:
```

cd /Desktop
sudo mv server.cfg /admin/srcds/cstrike/cfg/

```

You just needed superuser permissions to move the file into there. Ensure you also are changing that /admin directory example I gave you, to the path that you have to place it in :)

---

### Post by _mOrgoth_ on 2006-10-15
cd /Desktop
sudo mv server.cfg /admin/srcds/cstrike/cfg/

Tryed: Now it say: mv:target /admin/srcds/cstrike/cfg/ is not a directory: no such file or directory
When I try cd in terminal to it: cd cstrike Permission denied:-k

---

### Post by capn_hector on 2006-10-15
you need to type in the path for your machine.  if its /source/srcds/cstrike/cfg then the move wont work since /admin/... does not exits.  check the path and try it again.

---

### Post by _mOrgoth_ on 2006-10-16
Tryed...dont work..."I dont have permission" :evil:  I will install it again...

---

### Post by _mOrgoth_ on 2006-10-16
Ok... new installation of ubuntu... Same as first time. Now is everithing ok. It seams that permission problem was somekind of instalation bug.

---

