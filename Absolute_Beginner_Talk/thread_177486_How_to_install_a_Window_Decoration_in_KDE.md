---
title: "How to install a Window Decoration in KDE?"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by Christmas on 2006-05-16
I downloaded some windows decorations from [http://www.kde-look.org/]("http://www.kde-look.org/") and I read about using DeKorator but I can't compile the program. Is there an easy way of installing them, like copying the files to a certain folder so the window decoration will appear in the Control Center?

---

### Post by sphere02 on 2006-05-16
install dekorator:

sudo apt-get install dekorator

compile the decorations like:

./configure or ./configure --prefix=/usr/

make

sudo make install

---

### Post by ComplexNumber on 2006-05-16
make sure you get the right version of dekorator too. it can be extremely picky about what themes will work with it and which won't.
some(about 40-60%) window manager themes just wouldn't compile at all for me.

> 
Is there an easy way of installing them, like copying the files to a certain folder so the window decoration will appear in the Control Center? i set aside a directory dedicated to dekorator themes, and then just plonked them all in there. the themes based on dekorator usually have 3 parts - Masks, Buttons, Deco. to select a theme,  select dekorator in the theme manager, and use the browser to point to the masks, buttons, and deco.

welcome to the wonderful (and painful) world of KDE theming.

---

### Post by Ptero-4 on 2007-01-30
You don`t need to compile dekorator themes, they`re pixmap based (like the ones for metacity), if you get a theme and it says about compiling it`s a native kwin theme and not a dekorator one.

---

