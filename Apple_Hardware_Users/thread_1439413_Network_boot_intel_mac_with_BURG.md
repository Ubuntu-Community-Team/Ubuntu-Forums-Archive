---
title: "Network boot intel mac with BURG"
date: 2010-03-26
forum: Apple Hardware Users
---

### Post by bean123 on 2010-03-26
I just add netfs driver for EFI platform, you can now netboot linux on your intel macs.

First, you need to setup netboot server. Macs uses BSDP (Boot Service Discovery Protocol) which is a variation of DHCP. Google it and you can find guides on howto setup servers using OSX, Linux or Windows. My testing environment is a pacthed cygwin dhcp server on Windows.

Download 20100326 or latest burg-efi64 packages [http://code.google.com/p/burg/downloads/list](http://code.google.com/p/burg/downloads/list), extract it to you tftpboot root directory, and construct burg.cfg.

You can even start graphic menu, download the burg-themes package, extract to same directory as burg64.efi, and change efi_gui.cfg as:

```

set theme_name=ubuntu
function select_menu {
  if menu_popup -t template_popup theme_menu ; then
    free_config template_popup template_subitem menu
    load_config ${prefix}/themes/${theme_name}/theme
    menu_refresh
  fi
}
function toggle_fold {
  if test -z $theme_fold ; then
    set theme_fold=1
  else
    set theme_fold=
  fi
  menu_refresh
}
menu_region.text
load_string '+theme_menu { -chiva { command="set theme_name=chiva" }}'
load_string '+theme_menu { -minimum { command="set theme_name=minimum" }}'
load_string '+theme_menu { -proto { command="set theme_name=proto" }}'
load_string '+theme_menu { -radiance { command="set theme_name=radiance" }}'
load_string '+theme_menu { -radiancetext { command="set theme_name=radiancetext" }}'
load_string '+theme_menu { -refit { command="set theme_name=refit" }}'
load_string '+theme_menu { -sora { command="set theme_name=sora" }}'
load_string '+theme_menu { -sora_clean { command="set theme_name=sora_clean" }}'
load_string '+theme_menu { -sora_extended { command="set theme_name=sora_extended" }}'
load_string '+theme_menu { -ubuntu { command="set theme_name=ubuntu" }}'
load_string '+theme_menu { -ubuntu2 { command="set theme_name=ubuntu2" }}'
load_string '+theme_menu { -winter { command="set theme_name=winter" }}'
load_config ${prefix}/themes/conf.d/10_hotkey
load_config ${prefix}/themes/${theme_name}/theme
set gfxfont="Unifont Regular 16"
menu_region.gfx
controller.ext

```

You need to use "source efi_gui.cfg" from main burg.cfg.

To netboot your intel mac, press 'n' key at startup. The network device is (net0). New macs also have (net1) which could be the wireless card.

Note that you can access (net0), (net1) even when booting from local disk, but you still need to have a netboot server. For example, you can try this:

```

cat (net0)/burg.cfg

```

---

