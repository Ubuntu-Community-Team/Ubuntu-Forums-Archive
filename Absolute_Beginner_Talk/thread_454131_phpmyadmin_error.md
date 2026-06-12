---
title: "phpmyadmin error"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by ikkem on 2007-05-25
when I try to login i get this instead of the login screen....
I have php installed 
thanks in advance

>  
[http://127.0.0.1/phpmyadmin/](http://127.0.0.1/phpmyadmin/)

<?php
/* $Id: index.php 9718 2006-11-18 11:21:43Z lem9 $ */
// vim: expandtab sw=4 ts=4 sts=4:
/**
 * forms frameset
 *
 * @uses    libraries/common.lib.php        global fnctions
 * @uses    libraries/relation.lib.php      table relations
 * @uses    $GLOBALS['strNoFrames']
 * @uses    $GLOBALS['cfg']['QueryHistoryDB']
 * @uses    $GLOBALS['cfg']['Server']['user']
 * @uses    $GLOBALS['cfg']['DefaultTabServer']     as src for the mainframe
 * @uses    $GLOBALS['cfg']['DefaultTabDatabase']   as src for the mainframe
 * @uses    $GLOBALS['cfg']['NaviWidth']            for navi frame width
 * @uses    $GLOBALS['collation_connection']    from $_REQUEST (grab_globals.lib.php)
 *                                              or common.lib.php
 * @uses    $GLOBALS['available_languages'] from common.lib.php (select_lang.lib.php)
 * @uses    $GLOBALS['db']
 * @uses    $GLOBALS['charset']
 * @uses    $GLOBALS['lang']
 * @uses    $GLOBALS['text_dir']
 * @uses    $_ENV['HTTP_HOST']
 * @uses    PMA_getRelationsParam()
 * @uses    PMA_purgeHistory()
 * @uses    PMA_generate_common_url()
 * @uses    PMA_VERSION
 * @uses    session_write_close()
 * @uses    time()
 * @uses    PMA_getenv()
 * @uses    header()                to send charset
 */

/**
 * Gets core libraries and defines some variables
 */
require_once './libraries/common.lib.php';

/**
 * Includes the ThemeManager if it hasn't been included yet
 */
require_once './libraries/relation.lib.php';

// free the session file, for the other frames to be loaded
session_write_close();

// Gets the host name
// loic1 - 2001/25/11: use the new globals arrays defined with php 4.1+
if (empty($HTTP_HOST)) {
    if (PMA_getenv('HTTP_HOST')) {
        $HTTP_HOST = PMA_getenv('HTTP_HOST');
    } else {
        $HTTP_HOST = '';
    }
}


// purge querywindow history
$cfgRelation = PMA_getRelationsParam();
if ($GLOBALS['cfg']['QueryHistoryDB'] && $cfgRelation['historywork']) {
    PMA_purgeHistory( $GLOBALS['cfg']['Server']['user'] );
}
unset($cfgRelation); 

---

### Post by allllec on 2007-05-25
have you tested any other php documents? it looks like php is parsing. if you dont mind possibly loosing some settings or whatever it might be a good idea just to reinstall php/apache/phpmyadmin, thats usualy a quick fix to something like that :-)

good luck

ta

alec

---

