# Finishing Touches

One problem with metablocks is that they need to be added manually to the post so that a value for the post_meta field can be stored. This means that it is easy for an author to forget. Luckily, this can be solved by using [block templates](/docs/designers-developers/developers/block-api/block-templates.md). A block template is a predefined list of block items per post type. Templates allow you to specify a default initial state for a post type.

For this example, you use a template to automatically insert the meta block at the top of a post.

Add the following code to the `myguten-meta-block.php` file:

```php
function myguten_register_template() {
    $post_type_object = get_post_type_object( 'post' );
    $post_type_object->template = array(
        array( 'myguten/meta-block' ),
    );
}
add_action( 'init', 'myguten_register_template' );
```

You can also add other block types in the array, including placeholders, or even lock down a post to a set of specific blocks. Templates are a powerful tool for controlling the editing experience, see the documentation linked above for more.
