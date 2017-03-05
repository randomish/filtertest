# filtertest
##Filter tests

Quote from https://adblockplus.org/filters#special-comments on how the special comment _! Redirect_ should work:  
> ! Redirect: http://example.com/list.txt
>
>This comment indicates that the filter list has moved to a new download address. Adblock Plus will ignore any file contents beyond that comment and immediately try downloading from the new address. In case of success the address of the filter list will be updated in the settings. This comment is ignored if the new address is the same as the current address, meaning that it can be used to enforce the "canonical" address of the filter list.

In addition to that explanation, I also believe that when a redirect is performed (on list update), the client/extension should check if the new URL already is present in the custom filters, and if it is, just delete the duplicate list (don't leave old or new URL, only leave original entry for new URL in case it was manually disabled by user).

To test, just add https://raw.githubusercontent.com/randomish/filtertest/master/oldlistwithtitle.txt to your custom filters. If the redirect is successful, the entry should be automatically replaced by the new URL and the title changed to _New custom test list_.

2017-03-05:  
Adblock Plus 2.8.2 for Firefox - Redirect to new list works. New list visible in settings immediately.  
Adblock 3.8.8 for Chrome - Redirect to new list works. Have to close and reopen settings tab for changes to be visible.  
uBlock Origin 1.11.0 for Chrome - Redirect to new list does **not** work.

Additional feature request:  
I also wish that if the _! Redirect:_ is followed by just a newline (or whitespace then newline) that the list would be deleted from the extension settings. This way the list creator could signal that the list is dead and should be deleted automatically. This part is just my feature request and not implemented by any extension yet AFAIK. I created an example for this here: https://raw.githubusercontent.com/randomish/filtertest/master/deletelist.txt
