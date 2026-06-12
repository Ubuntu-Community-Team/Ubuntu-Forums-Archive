---
title: "Giving permissions to a directory tree"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by cafevincent on 2005-11-10
I've been copying my files off ntfs partitions and when they are copied I must apply permissions to every folder and subfolder. It's a overwhelming job. There must be a better way I'm sure so please post your suggestions.

---

### Post by Kyral on 2005-11-10
chmod -R <permissions> <folder>

---

### Post by Lambert on 2005-11-10
Not sure what method you're using to change permissions but from the command line you add the recursive option so it would be something like this.

```
sudo chmod -R <###> <starting_directory>
```

# = the permission code you want to set such as 755 etc...

This command takes the permission you set for this directory and applies it to every child directory/folder under this directory.

If this sounds confusing to you try going to [[COLOR="Blue"]this[/COLOR]]("http://www.linux-tutorial.info/modules.php?name=Tutorial&pageid=225") page and read up on permissions. Small tutorial for using command line to set permissions.

For more help type [COLOR="DarkRed"]chmod help[/COLOR] or something similar in google to find more info.

---

### Post by cafevincent on 2005-11-10
[QUOTE=Kyral]chmod -R <permissions> <folder>[/QUOTE]

What can I use for <permissions>, chmod --help doesn't say much or I'm just not understanding it. I need to add write permission for owner.

---

### Post by David Marrs on 2005-11-10
you want to add write permission, so you type '+w' as an option.
```
chmod -R +w /path/to/folder/
```

If you wanted to remove write permissions, then you'd type -w, to make it the only permission, you'd type =w, and so on. I'm getting this from the man file, btw. Type 'man chmod'. The manual style is terse, but understandable once you get used to it (get used to it, because it's not going to change!).

---

### Post by cafevincent on 2005-11-10
[QUOTE=David Marrs]you want to add write permission, so you type '+w' as an option.
```
chmod -R +w /path/to/folder/
```

If you wanted to remove write permissions, then you'd type -w, to make it the only permission, you'd type =w, and so on. I'm getting this from the man file, btw. Type 'man chmod'. The manual style is terse, but understandable once you get used to it (get used to it, because it's not going to change!).[/QUOTE]

Thanks!

---

