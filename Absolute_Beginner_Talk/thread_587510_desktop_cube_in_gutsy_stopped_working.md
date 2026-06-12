---
title: "desktop cube in gutsy stopped working"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by limac on 2007-10-22
i was really enjoying the cube and I forgot what I did and the cube and the cube now won't rotate. Now even if I go enable the expo on one window shows up and there used to be two. And my desktop cube and rotate cube are both enabled.And everything else works perfect. What I think is that somehow i change the two workspaces to one and that's why it's not rotating? Or what? I am not very sure.

thnx

---

### Post by Microsoft_Sam on 2007-10-22
Are your other Compiz effects broken as well? Try Alt+F2 and typing in compiz

---

### Post by Faud on 2007-10-23
If you think that you changed the number of desktops that you have. Go to your compiz settings manager and then the "general" tab. For four desktops it should look like
4
1
1

---

### Post by brownbat on 2007-11-02
I've found the switcher doesn't work for me unless I reset the number of desktops manually, as suggested [url=
http://compiz.org/Workspace_Switcher_Fix]here[/url]:

```

gconftool-2 -s /apps/compiz/general/screen0/options/number_of_desktops "2" --type=int &&
sleep 1 &&
gconftool-2 -s /apps/compiz/general/screen0/options/number_of_desktops "1" --type=int

```

---

