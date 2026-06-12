---
title: "Realy new to Linux.... Easy file install question"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by Alias- Human on 2006-11-25
I just DL'ed the "Vulture's Eye" thing for NetHack. I used the Archive Manager to unzip it to my desktop. Now I have a file on my desktop called "vultures-2.1.0". Can somebody tell me (nicely) what to do with it from here?

Or better yet, Can you point me in the direction of a tutorial/doc that will tell me how to deal with this instalation stuff?

I really appretiate you time with this even though to most of you it is a very simple thing.
Thanks,
AHDRL

---

### Post by junglepeanut on 2006-11-25
Normally for applications etc, you will use synaptic ( a graphical interface ) to download programs. Or you can use apt-get or aptitude for a command line  installation of those same repositories. Search the wiki for repositories and that will be your best bet for learning how to get programs for Ubuntu.

I am searching google to figure out what this vultures eye is.

---

### Post by junglepeanut on 2006-11-25
Ok, this may actually not be entirely easy for a first install. Nethack is in synaptic though.

Normally you can get almost everything from the repositories but this is pretty new. So I have not downloaded it. What you are going to want to do is once you have it uncompressed look for a file that says README and a file that says INSTALL they will probably say something along the lines of 

configure
then
make
then 
make install
 but check in those files.

Also somebody probably has a repository for it as it looks somewhat interesting,so you could probably use synaptic if you can find it, I just did not look hard at all.

---

### Post by tribaal on 2006-11-25
You probably downloaded source code for the program you're trying to install.
Source usually comes in a tar.gz package (basically, a ziped directory).

Once you unzipped the source, open a terminal, and move to the unzipped folder.

In there, the magic command-lines to enter are usually:

> ./configure
make
sudo make install

This *should* install the program from source. It will compile the source code into a binary executable, so you'll need to install the "build-essentials" package (via synaptic or with "sudo apt-get install build-essentials").

I've looked around for a decent tutorial on how to build stuff from source, but I couldn't find any. Somebody else might point you to a good one... Asyu?

Hope this helps... :)

- trib'

---

### Post by junglepeanut on 2006-11-25
Also he seems to have a script that will do all of that for you on his site...so you maybe able to just run that, if not back to the commands I suggested and reading the readme.

If you have not installed anything on your computer yet, you may need the package 

build-essential

so choose it from synaptic by clicking it and applying or us the terminal

sudo aptitude install build-essential

this gives all sorts of compiling tools.

---

### Post by Alias- Human on 2006-11-25
Thanks for your quick responce **junglepeanut**.
the basic description can be found at; [http://www.answers.com/topic/vulture-s](http://www.answers.com/topic/vulture-s)
and the download place where I found it is; [http://old.darkarts.co.za/projects/vultures/downloads/](http://old.darkarts.co.za/projects/vultures/downloads/)

They have a "repository" listed. So If I just add that to my repository list it will show up in my synaptic? and then it will install itself?

---

### Post by Alias- Human on 2006-11-25
Wow, you type fast!

Thanks for the info **junglepeanut**, I'm going to try all that right now.
it'll take me some time though,(I'm kind of slow at this).

Thanks again,
AHDRL

---

### Post by junglepeanut on 2006-11-25
No problem, I think tribaal gave a more succinct answer than mine, but I get lazy late in the night.

Yes, if you have it in your source.list, aptitude should find all dependencies. (fingers crossed)

---

### Post by junglepeanut on 2006-11-25
[http://www.ubuntuforums.org/showthread.php?t=202476](http://www.ubuntuforums.org/showthread.php?t=202476)


This post shows that awhile ago people had a problem doing the make blah blah, (might have been a simple mistake as it is not complete listing of error) but quite a few posts points to this as resolving the issue.

I would probably still find a way to do configure make etc, or use the install script that the guy has on his site. As far as repositories go, it looks like he is now using something called darcs and another called subversion. You can get subversion from synaptic, but I have never felt the need to use it, so you may need to ask someone else how to do that as I have little experience.

---

### Post by Alias- Human on 2006-11-25
I did not mean to slight you **Tribaal**, it's late at night for me as well (*sleepy, blurry eyes). Thanks for your help!

I tried to -> cd (to the file)/vultures-2.1.0

and then; ./configure
and it said it didn't find that in there.

I went back to the site and I couldn't find the thing that I thought was a repository address (probably read it wrong at first) so I DL'ed the unix install file.
It is a .bin.sh file ... ?  (this is me having no clue) I'll try to click on it and if that doesn't do anything productive I'll type it into the shell and see if it executes.

---

### Post by junglepeanut on 2006-11-25
Cool, some times maintainers do not put a configure script inside their programs, normally the configure checks which compiler you are using and other stuff to make sure it will compile properly as most compilers have similar flags but sometimes one flag is different than another compiler sometimes even versions change flags or way things are handled.

So try the next two in the folder.

The script probably runs with just a 

./thescriptsname

You may need to make it executable first though, and if using edgy may need to make a fake link for bash. But in dapper you should be fine just

chmod 755 thescriptname
./thescriptsname

---

### Post by Alias- Human on 2006-11-26
Thanks **junglepeanut**, that seamed to work but I got back a lot of problem and warning statements. The windows.exe worked on my windows hard drive (I hardly ever use that any more so it won't get much play time) but the installation here in Ubuntu produced the following errors;

> Setup NetHack build environment ...
Building and installing NetHack in /home/ghost/vultures/vultureseyedir
util/tiletrans.c:11:17: error: png.h: No such file or directory
util/tiletrans.c:84: error: syntax error before ‘*’ token
util/tiletrans.c: In function ‘freeimg’:
util/tiletrans.c:87: error: ‘img’ undeclared (first use in this function)
util/tiletrans.c:87: error: (Each undeclared identifier is reported only once
util/tiletrans.c:87: error: for each function it appears in.)
util/tiletrans.c:88: error: ‘height’ undeclared (first use in this function)
util/tiletrans.c: At top level:
util/tiletrans.c:101: error: syntax error before ‘png_byte’
util/tiletrans.c: In function ‘read_png_file’:
util/tiletrans.c:104: error: ‘filename’ undeclared (first use in this function)
util/tiletrans.c:106: error: ‘png_structp’ undeclared (first use in this function)
util/tiletrans.c:106: error: syntax error before ‘png_ptr’
util/tiletrans.c:107: error: ‘png_infop’ undeclared (first use in this function)util/tiletrans.c:119: warning: implicit declaration of function ‘png_sig_cmp’
util/tiletrans.c:126: error: ‘png_ptr’ undeclared (first use in this function)
util/tiletrans.c:126: warning: implicit declaration of function ‘png_create_read_struct’
util/tiletrans.c:126: error: ‘PNG_LIBPNG_VER_STRING’ undeclared (first use in this function)
util/tiletrans.c:129: error: ‘info_ptr’ undeclared (first use in this function)
util/tiletrans.c:129: warning: implicit declaration of function ‘png_create_info_struct’
util/tiletrans.c:133: warning: implicit declaration of function ‘png_destroy_read_struct’
util/tiletrans.c:133: error: ‘png_infopp_NULL’ undeclared (first use in this function)
util/tiletrans.c:138: warning: implicit declaration of function ‘setjmp’
util/tiletrans.c:138: warning: implicit declaration of function ‘png_jmpbuf’
util/tiletrans.c:148: warning: implicit declaration of function ‘png_init_io’
util/tiletrans.c:151: warning: implicit declaration of function ‘png_set_sig_bytes’
util/tiletrans.c:154: warning: implicit declaration of function ‘png_read_info’
util/tiletrans.c:156: warning: implicit declaration of function ‘png_get_IHDR’
util/tiletrans.c:156: error: ‘width’ undeclared (first use in this function)
util/tiletrans.c:156: error: ‘height’ undeclared (first use in this function)
util/tiletrans.c:159: warning: implicit declaration of function ‘png_get_valid’
util/tiletrans.c:159: error: ‘PNG_INFO_PLTE’ undeclared (first use in this function)
util/tiletrans.c:165: warning: implicit declaration of function ‘png_set_expand’util/tiletrans.c:166: warning: implicit declaration of function ‘png_set_filler’util/tiletrans.c:166: error: ‘PNG_FILLER_AFTER’ undeclared (first use in this function)
util/tiletrans.c:167: error: ‘PNG_COLOR_MASK_ALPHA’ undeclared (first use in this function)
util/tiletrans.c:170: warning: implicit declaration of function ‘png_read_update_info’
util/tiletrans.c:172: error: ‘image’ undeclared (first use in this function)
util/tiletrans.c:172: error: ‘png_byte’ undeclared (first use in this function)
util/tiletrans.c:172: error: syntax error before ‘)’ token
util/tiletrans.c:174: warning: implicit declaration of function ‘png_get_rowbytes’
util/tiletrans.c:176: warning: implicit declaration of function ‘png_read_image’util/tiletrans.c: At top level:
util/tiletrans.c:211: error: syntax error before ‘png_byte’
util/tiletrans.c: In function ‘write_png_file’:
util/tiletrans.c:213: error: ‘png_structp’ undeclared (first use in this function)
util/tiletrans.c:213: error: syntax error before ‘png_ptr’
util/tiletrans.c:214: error: ‘png_infop’ undeclared (first use in this function)util/tiletrans.c:216: error: ‘png_ptr’ undeclared (first use in this function)
util/tiletrans.c:216: warning: implicit declaration of function ‘png_create_write_struct’
util/tiletrans.c:216: error: ‘PNG_LIBPNG_VER_STRING’ undeclared (first use in this function)
util/tiletrans.c:217: error: ‘info_ptr’ undeclared (first use in this function)
util/tiletrans.c:222: warning: implicit declaration of function ‘png_destroy_write_struct’
util/tiletrans.c:226: error: ‘outfile’ undeclared (first use in this function)
util/tiletrans.c:228: warning: implicit declaration of function ‘png_set_IHDR’
util/tiletrans.c:228: error: ‘width’ undeclared (first use in this function)
util/tiletrans.c:228: error: ‘height’ undeclared (first use in this function)
util/tiletrans.c:228: error: ‘PNG_COLOR_TYPE_RGB_ALPHA’ undeclared (first use in this function)
util/tiletrans.c:229: error: ‘PNG_INTERLACE_NONE’ undeclared (first use in this function)
util/tiletrans.c:229: error: ‘PNG_COMPRESSION_TYPE_BASE’ undeclared (first use in this function)
util/tiletrans.c:229: error: ‘PNG_FILTER_TYPE_BASE’ undeclared (first use in this function)
util/tiletrans.c:231: warning: implicit declaration of function ‘png_write_info’util/tiletrans.c:232: warning: implicit declaration of function ‘png_write_image’
util/tiletrans.c:232: error: ‘tile’ undeclared (first use in this function)
util/tiletrans.c:233: warning: implicit declaration of function ‘png_write_end’
util/tiletrans.c: At top level:
util/tiletrans.c:246: error: syntax error before ‘*’ token
util/tiletrans.c:246: error: syntax error before ‘*’ token
util/tiletrans.c:248: warning: return type defaults to ‘int’
util/tiletrans.c: In function ‘grab_tile’:
util/tiletrans.c:249: error: ‘png_byte’ undeclared (first use in this function)
util/tiletrans.c:249: error: ‘tile’ undeclared (first use in this function)
util/tiletrans.c:250: error: ‘img’ undeclared (first use in this function)
util/tiletrans.c:252: error: ‘tile_y’ undeclared (first use in this function)
util/tiletrans.c:252: error: ‘tile_x’ undeclared (first use in this function)
util/tiletrans.c:260: error: ‘tile_h’ undeclared (first use in this function)
util/tiletrans.c:260: error: ‘tile_w’ undeclared (first use in this function)
util/tiletrans.c:269: error: ‘img_h’ undeclared (first use in this function)
util/tiletrans.c:277: error: ‘img_w’ undeclared (first use in this function)
util/tiletrans.c:328: error: ‘hs_x’ undeclared (first use in this function)
util/tiletrans.c:329: error: ‘hs_y’ undeclared (first use in this function)
util/tiletrans.c:331: error: syntax error before ‘)’ token
util/tiletrans.c: In function ‘load_tiles’:
util/tiletrans.c:370: error: ‘png_uint_32’ undeclared (first use in this function)
util/tiletrans.c:370: error: syntax error before ‘width’
util/tiletrans.c:371: error: ‘png_byte’ undeclared (first use in this function)
util/tiletrans.c:371: error: ‘img’ undeclared (first use in this function)
util/tiletrans.c:372: error: ‘tile’ undeclared (first use in this function)
util/tiletrans.c:395: error: ‘height’ undeclared (first use in this function)
util/tiletrans.c:400: error: ‘width’ undeclared (first use in this function)
In file included from vultures_win_event.c:11:
vultures_map.h:10:32: error: vultures_gametiles.h: No such file or directory
In file included from vultures_win_event.c:13:
vultures_txt.h:7:21: error: SDL_ttf.h: No such file or directory
In file included from vultures_win.c:14:
vultures_map.h:10:32: error: vultures_gametiles.h: No such file or directory
In file included from vultures_win.c:16:
vultures_txt.h:7:21: error: SDL_ttf.h: No such file or directory
vultures_txt.c:9:21: error: SDL_ttf.h: No such file or directory
In file included from vultures_tile.c:12:
vultures_map.h:10:32: error: vultures_gametiles.h: No such file or directory
In file included from vultures_opt.c:17:
vultures_map.h:10:32: error: vultures_gametiles.h: No such file or directory
In file included from vultures_mou.c:14:
vultures_txt.h:7:21: error: SDL_ttf.h: No such file or directory
vultures_mou.c:16:32: error: vultures_gametiles.h: No such file or directory
In file included from vultures_map.c:6:
vultures_map.h:10:32: error: vultures_gametiles.h: No such file or directory
In file included from vultures_map.c:13:
vultures_txt.h:7:21: error: SDL_ttf.h: No such file or directory
vultures_main.c:28:32: error: vultures_gametiles.h: No such file or directory
In file included from vultures_main.c:41:
vultures_txt.h:7:21: error: SDL_ttf.h: No such file or directory
In file included from vultures_init.c:9:
vultures_map.h:10:32: error: vultures_gametiles.h: No such file or directory
In file included from vultures_init.c:15:
vultures_txt.h:7:21: error: SDL_ttf.h: No such file or directory
vultures_gfl.c:16:17: error: png.h: No such file or directory
util/tiletrans.c:11:17: error: png.h: No such file or directory
util/tiletrans.c:84: error: syntax error before ‘*’ token
util/tiletrans.c: In function ‘freeimg’:
util/tiletrans.c:87: error: ‘img’ undeclared (first use in this function)
util/tiletrans.c:87: error: (Each undeclared identifier is reported only once
util/tiletrans.c:87: error: for each function it appears in.)
util/tiletrans.c:88: error: ‘height’ undeclared (first use in this function)
util/tiletrans.c: At top level:
util/tiletrans.c:101: error: syntax error before ‘png_byte’
util/tiletrans.c: In function ‘read_png_file’:
util/tiletrans.c:104: error: ‘filename’ undeclared (first use in this function)
util/tiletrans.c:106: error: ‘png_structp’ undeclared (first use in this function)
util/tiletrans.c:106: error: syntax error before ‘png_ptr’
util/tiletrans.c:107: error: ‘png_infop’ undeclared (first use in this function)util/tiletrans.c:119: warning: implicit declaration of function ‘png_sig_cmp’
util/tiletrans.c:126: error: ‘png_ptr’ undeclared (first use in this function)
util/tiletrans.c:126: warning: implicit declaration of function ‘png_create_read_struct’
util/tiletrans.c:126: error: ‘PNG_LIBPNG_VER_STRING’ undeclared (first use in this function)
util/tiletrans.c:129: error: ‘info_ptr’ undeclared (first use in this function)
util/tiletrans.c:129: warning: implicit declaration of function ‘png_create_info_struct’
util/tiletrans.c:133: warning: implicit declaration of function ‘png_destroy_read_struct’
util/tiletrans.c:133: error: ‘png_infopp_NULL’ undeclared (first use in this function)
util/tiletrans.c:138: warning: implicit declaration of function ‘setjmp’
util/tiletrans.c:138: warning: implicit declaration of function ‘png_jmpbuf’
util/tiletrans.c:148: warning: implicit declaration of function ‘png_init_io’
util/tiletrans.c:151: warning: implicit declaration of function ‘png_set_sig_bytes’
util/tiletrans.c:154: warning: implicit declaration of function ‘png_read_info’
util/tiletrans.c:156: warning: implicit declaration of function ‘png_get_IHDR’
util/tiletrans.c:156: error: ‘width’ undeclared (first use in this function)
util/tiletrans.c:156: error: ‘height’ undeclared (first use in this function)
util/tiletrans.c:159: warning: implicit declaration of function ‘png_get_valid’
util/tiletrans.c:159: error: ‘PNG_INFO_PLTE’ undeclared (first use in this function)
util/tiletrans.c:165: warning: implicit declaration of function ‘png_set_expand’util/tiletrans.c:166: warning: implicit declaration of function ‘png_set_filler’util/tiletrans.c:166: error: ‘PNG_FILLER_AFTER’ undeclared (first use in this function)
util/tiletrans.c:167: error: ‘PNG_COLOR_MASK_ALPHA’ undeclared (first use in this function)
util/tiletrans.c:170: warning: implicit declaration of function ‘png_read_update_info’
util/tiletrans.c:172: error: ‘image’ undeclared (first use in this function)
util/tiletrans.c:172: error: ‘png_byte’ undeclared (first use in this function)
util/tiletrans.c:172: error: syntax error before ‘)’ token
util/tiletrans.c:174: warning: implicit declaration of function ‘png_get_rowbytes’
util/tiletrans.c:176: warning: implicit declaration of function ‘png_read_image’util/tiletrans.c: At top level:
util/tiletrans.c:211: error: syntax error before ‘png_byte’
util/tiletrans.c: In function ‘write_png_file’:
util/tiletrans.c:213: error: ‘png_structp’ undeclared (first use in this function)
util/tiletrans.c:213: error: syntax error before ‘png_ptr’
util/tiletrans.c:214: error: ‘png_infop’ undeclared (first use in this function)util/tiletrans.c:216: error: ‘png_ptr’ undeclared (first use in this function)
util/tiletrans.c:216: warning: implicit declaration of function ‘png_create_write_struct’
util/tiletrans.c:216: error: ‘PNG_LIBPNG_VER_STRING’ undeclared (first use in this function)
util/tiletrans.c:217: error: ‘info_ptr’ undeclared (first use in this function)
util/tiletrans.c:222: warning: implicit declaration of function ‘png_destroy_write_struct’
util/tiletrans.c:226: error: ‘outfile’ undeclared (first use in this function)
util/tiletrans.c:228: warning: implicit declaration of function ‘png_set_IHDR’
util/tiletrans.c:228: error: ‘width’ undeclared (first use in this function)
util/tiletrans.c:228: error: ‘height’ undeclared (first use in this function)
util/tiletrans.c:228: error: ‘PNG_COLOR_TYPE_RGB_ALPHA’ undeclared (first use in this function)
util/tiletrans.c:229: error: ‘PNG_INTERLACE_NONE’ undeclared (first use in this function)
util/tiletrans.c:229: error: ‘PNG_COMPRESSION_TYPE_BASE’ undeclared (first use in this function)
util/tiletrans.c:229: error: ‘PNG_FILTER_TYPE_BASE’ undeclared (first use in this function)
util/tiletrans.c:231: warning: implicit declaration of function ‘png_write_info’util/tiletrans.c:232: warning: implicit declaration of function ‘png_write_image’
util/tiletrans.c:232: error: ‘tile’ undeclared (first use in this function)
util/tiletrans.c:233: warning: implicit declaration of function ‘png_write_end’
util/tiletrans.c: At top level:
util/tiletrans.c:246: error: syntax error before ‘*’ token
util/tiletrans.c:246: error: syntax error before ‘*’ token
util/tiletrans.c:248: warning: return type defaults to ‘int’
util/tiletrans.c: In function ‘grab_tile’:
util/tiletrans.c:249: error: ‘png_byte’ undeclared (first use in this function)
util/tiletrans.c:249: error: ‘tile’ undeclared (first use in this function)
util/tiletrans.c:250: error: ‘img’ undeclared (first use in this function)
util/tiletrans.c:252: error: ‘tile_y’ undeclared (first use in this function)
util/tiletrans.c:252: error: ‘tile_x’ undeclared (first use in this function)
util/tiletrans.c:260: error: ‘tile_h’ undeclared (first use in this function)
util/tiletrans.c:260: error: ‘tile_w’ undeclared (first use in this function)
util/tiletrans.c:269: error: ‘img_h’ undeclared (first use in this function)
util/tiletrans.c:277: error: ‘img_w’ undeclared (first use in this function)
util/tiletrans.c:328: error: ‘hs_x’ undeclared (first use in this function)
util/tiletrans.c:329: error: ‘hs_y’ undeclared (first use in this function)
util/tiletrans.c:331: error: syntax error before ‘)’ token
util/tiletrans.c: In function ‘load_tiles’:
util/tiletrans.c:370: error: ‘png_uint_32’ undeclared (first use in this function)
util/tiletrans.c:370: error: syntax error before ‘width’
util/tiletrans.c:371: error: ‘png_byte’ undeclared (first use in this function)
util/tiletrans.c:371: error: ‘img’ undeclared (first use in this function)
util/tiletrans.c:372: error: ‘tile’ undeclared (first use in this function)
util/tiletrans.c:395: error: ‘height’ undeclared (first use in this function)
util/tiletrans.c:400: error: ‘width’ undeclared (first use in this function)
In file included from vultures_win_event.c:11:
vultures_map.h:10:32: error: vultures_gametiles.h: No such file or directory
In file included from vultures_win_event.c:13:
vultures_txt.h:7:21: error: SDL_ttf.h: No such file or directory
In file included from vultures_win.c:14:
vultures_map.h:10:32: error: vultures_gametiles.h: No such file or directory
In file included from vultures_win.c:16:
vultures_txt.h:7:21: error: SDL_ttf.h: No such file or directory
vultures_txt.c:9:21: error: SDL_ttf.h: No such file or directory
In file included from vultures_tile.c:12:
vultures_map.h:10:32: error: vultures_gametiles.h: No such file or directory
In file included from vultures_opt.c:17:
vultures_map.h:10:32: error: vultures_gametiles.h: No such file or directory
In file included from vultures_mou.c:14:
vultures_txt.h:7:21: error: SDL_ttf.h: No such file or directory
vultures_mou.c:16:32: error: vultures_gametiles.h: No such file or directory
In file included from vultures_map.c:6:
vultures_map.h:10:32: error: vultures_gametiles.h: No such file or directory
In file included from vultures_map.c:13:
vultures_txt.h:7:21: error: SDL_ttf.h: No such file or directory
vultures_main.c:28:32: error: vultures_gametiles.h: No such file or directory
In file included from vultures_main.c:41:
vultures_txt.h:7:21: error: SDL_ttf.h: No such file or directory
In file included from vultures_init.c:9:
vultures_map.h:10:32: error: vultures_gametiles.h: No such file or directory
In file included from vultures_init.c:15:
vultures_txt.h:7:21: error: SDL_ttf.h: No such file or directory
vultures_gfl.c:16:17: error: png.h: No such file or directory
vultures_gfl.c:14:23: error: SDL_image.h: No such file or directory
vultures_gfl.c:16:17: error: png.h: No such file or directory
vultures_gfl.c:27: error: syntax error before ‘png_ptr’
vultures_gfl.c: In function ‘vultures_png_read_callback’:
vultures_gfl.c:29: error: ‘png_ptr’ undeclared (first use in this function)
vultures_gfl.c:29: error: (Each undeclared identifier is reported only once
vultures_gfl.c:29: error: for each function it appears in.)
vultures_gfl.c:30: error: ‘area’ undeclared (first use in this function)
vultures_gfl.c:30: error: ‘size’ undeclared (first use in this function)
vultures_gfl.c: In function ‘vultures_load_surface’:
vultures_gfl.c:42: error: ‘png_structp’ undeclared (first use in this function)
vultures_gfl.c:42: error: syntax error before ‘png_ptr’
vultures_gfl.c:43: error: ‘png_infop’ undeclared (first use in this function)
vultures_gfl.c:45: error: ‘png_uint_32’ undeclared (first use in this function)
vultures_gfl.c:45: error: syntax error before ‘width’
vultures_gfl.c:47: error: ‘png_bytep’ undeclared (first use in this function)
vultures_gfl.c:47: error: ‘row_pointers’ undeclared (first use in this function)vultures_gfl.c:62: warning: implicit declaration of function ‘png_sig_cmp’
vultures_gfl.c:66: error: ‘png_ptr’ undeclared (first use in this function)
vultures_gfl.c:66: warning: implicit declaration of function ‘png_create_read_struct’
vultures_gfl.c:66: error: ‘PNG_LIBPNG_VER_STRING’ undeclared (first use in this function)
vultures_gfl.c:71: error: ‘info_ptr’ undeclared (first use in this function)
vultures_gfl.c:71: warning: implicit declaration of function ‘png_create_info_struct’
vultures_gfl.c:76: warning: implicit declaration of function ‘setjmp’
vultures_gfl.c:79: warning: implicit declaration of function ‘png_set_read_fn’
vultures_gfl.c:82: warning: implicit declaration of function ‘png_read_info’
vultures_gfl.c:83: warning: implicit declaration of function ‘png_get_IHDR’
vultures_gfl.c:83: error: ‘width’ undeclared (first use in this function)
vultures_gfl.c:83: error: ‘height’ undeclared (first use in this function)
vultures_gfl.c:87: warning: implicit declaration of function ‘png_set_strip_16’
vultures_gfl.c:91: warning: implicit declaration of function ‘png_set_expand’
vultures_gfl.c:94: warning: implicit declaration of function ‘png_set_gray_to_rgb’
vultures_gfl.c:97: warning: implicit declaration of function ‘png_set_filler’
vultures_gfl.c:97: error: ‘PNG_FILLER_AFTER’ undeclared (first use in this function)
vultures_gfl.c:98: error: ‘PNG_COLOR_MASK_ALPHA’ undeclared (first use in this function)
vultures_gfl.c:129: error: syntax error before ‘Uint8’
vultures_gfl.c:132: warning: implicit declaration of function ‘png_read_image’
vultures_gfl.c:135: warning: implicit declaration of function ‘png_destroy_read_struct’
vultures_gfl.c:149: warning: control reaches end of non-void function
vultures_gfl.c: In function ‘vultures_save_png’:
vultures_gfl.c:204: error: ‘png_structp’ undeclared (first use in this function)vultures_gfl.c:204: error: syntax error before ‘png_ptr’
vultures_gfl.c:205: error: ‘png_infop’ undeclared (first use in this function)
vultures_gfl.c:209: error: ‘png_byte’ undeclared (first use in this function)
vultures_gfl.c:209: error: ‘image’ undeclared (first use in this function)
vultures_gfl.c:209: error: syntax error before ‘)’ token
vultures_gfl.c:231: error: ‘png_ptr’ undeclared (first use in this function)
vultures_gfl.c:231: warning: implicit declaration of function ‘png_create_write_struct’
vultures_gfl.c:231: error: ‘PNG_LIBPNG_VER_STRING’ undeclared (first use in this function)
vultures_gfl.c:232: error: ‘info_ptr’ undeclared (first use in this function)
vultures_gfl.c:233: warning: implicit declaration of function ‘png_jmpbuf’
vultures_gfl.c:237: warning: implicit declaration of function ‘png_init_io’
vultures_gfl.c:238: warning: implicit declaration of function ‘png_set_IHDR’
vultures_gfl.c:238: error: ‘PNG_COLOR_TYPE_RGBA’ undeclared (first use in this function)
vultures_gfl.c:238: error: ‘PNG_COLOR_TYPE_RGB’ undeclared (first use in this function)
vultures_gfl.c:239: error: ‘PNG_INTERLACE_NONE’ undeclared (first use in this function)
vultures_gfl.c:239: error: ‘PNG_COMPRESSION_TYPE_BASE’ undeclared (first use in this function)
vultures_gfl.c:239: error: ‘PNG_FILTER_TYPE_BASE’ undeclared (first use in this function)
vultures_gfl.c:240: warning: implicit declaration of function ‘png_set_rows’
vultures_gfl.c:241: warning: implicit declaration of function ‘png_write_png’
vultures_gfl.c:242: warning: implicit declaration of function ‘png_destroy_write_struct’
make[3]: *** [build_n/vultures_gfl.o] Error 1
make[2]: *** [../win/vultures/build_n/vultures.o] Error 2
make[1]: *** [vultureseye] Error 2
make: *** [nethack-home] Error 2


Thanks for the try anyways folks.
(this must be why it's not a part of deb-packages). It is an RPM package but I couldn't DL it for some reason, I was going to try using 'Alien' (I think it is called 'Alien'... changes rpm's to deb's, A whole other collage course for me :???: )

Thanks again,
AHDRL

---

### Post by junglepeanut on 2006-11-26
Yeah, if you found an rpm look up how to use the alien program, I have seen many posts saying that alien worked for them for various program installations. hope you get this figured out.

---

### Post by Tharquil on 2007-01-10
Here's how i managed to do it.
[http://www.ubuntuforums.com/showthread.php?t=335262](http://www.ubuntuforums.com/showthread.php?t=335262)

---

