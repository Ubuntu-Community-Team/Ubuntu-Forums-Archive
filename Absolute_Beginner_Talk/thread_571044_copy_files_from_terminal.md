---
title: "copy files from terminal"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Pabx on 2007-10-08
Hi , i want to copy a Folder Called vmware from Desktop to /media/IOMEGA_HDD but I cant cuz i need to be superuser, how can i do it from the terminal?

---

### Post by sumguy231 on 2007-10-08
```
sudo cp -r vmware /media/IOMEGA_HDD
```

---

### Post by aktiwers on 2007-10-08
```
cp -R Desktop/vmware /media/IOMEGA_HDD
```

---

### Post by ThrobbingBrain66 on 2007-10-08
sudo cp -r /Desktop/vmware/ /media/IOMEGA_HDD/

---

