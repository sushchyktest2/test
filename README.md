
## Controllers

* #### Single names should be used for controllers. 
 
* #### Method names from resoursfull controllers should be used:
  
  Bad:
    <pre><code>  class <del>ClubsController</del>
    {
        public function <del>showFormForCreating()</del> {}
        public function <del>saveClub()</del> {}        
        public function <del>updateClub()</del> {}
        public function <del>subscripeToClub()</del> {}
        public function <del>unsubscribeFromClub()</del>{}
        public function <del>deleteClub()</del>
    }</code></pre>
    
    
  Good:
    
        class ClubController
        {
            public function index() {}
            public function show() {}
            public function store() {}
            public function create() {}
            public function edit() {}
            public function update() {}
            public function destroy() {}
        }
 
        class ClubSubscriptionController
        {
             public function store(Request $request) {}
             public function destroy(Request $request) {}
        }
        
* #### Validation should be moved into Form Requests:
  Bad:  
  <pre><code>  public function update(Request $request) 
    {
        <del>$this->validate($request->all(), [</del>
          <del>'name' => 'required',</del>
          <del>'description' => 'required'</del>
        ]</del>
    ...</pre></code>
    
    
  Good:
    
        public function update(UpdatePost $request)
        {
        ...
        
* #### Form Requests should be follow controller and mehtod name:
        class CommentController
        { 
            public function store() {}
        }
  Bad:  
  <pre><code>
    class <del>commentSavePostReqeust</del> {}
    
    class <del>saveCommentPostRequest</del> {}
    
    class <del>createCommentRequest</del> {}
    
    class <del>newCommentRequest</del> {}
  </pre></code>
    
  Good:
  
        class UpdateCommentRequest {}


        
### Routes

Good: 
```
Route::prefix('user_profile')->group(function() {
    Route::get('{user}', 'UserProfileController@show);    
    Route::put('{user}', 'UserProfileController@update);    
})

Route::resource('users')->name('user_profile)->only(['show', 'update']);


Route::post('clubs/{club}/subscriptions', 'ClubSubscription@store');
Route::delete('clubs/{club}/subscriptions, 'ClasdsadasdubSubscriptionController@delete');
```

### Other
* Use camel case for variable names, name 
Good: `$getUsersQuery`, `` 

Bad: `$users`
