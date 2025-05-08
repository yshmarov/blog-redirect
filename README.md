# Blog Redirect Service

This service redirects all traffic from `blog.corsego.com` to `blog.superails.com` while preserving the original path and query parameters.

## Deployment to GitHub Pages

1. Create a new repository on GitHub

2. Push these files to your repository:

   - `index.html` (handles root path)
   - `404.html` (handles all other paths)

3. Go to your repository settings:

   - Navigate to "Settings" > "Pages"
   - Under "Source", select "Deploy from a branch"
   - Select "main" branch and "/ (root)" folder
   - Click "Save"

4. Configure your DNS settings:

   - Add a CNAME record in your DNS settings pointing `blog.corsego.com` to `yourusername.github.io`
   - In your GitHub repository settings, add `blog.corsego.com` as a custom domain

5. Wait for DNS propagation (can take up to 24 hours)

## How it works

The solution uses two files:

- `index.html`: Handles the root path (`/`) and includes a meta refresh as a fallback
- `404.html`: Handles all other paths by capturing the current URL and redirecting to the corresponding path on blog.superails.com

This setup ensures that all paths are properly redirected, including:

- Root path: `blog.corsego.com` → `blog.superails.com`
- Subpaths: `blog.corsego.com/about` → `blog.superails.com/about`
- Deep paths: `blog.corsego.com/posts/123` → `blog.superails.com/posts/123`
- Query parameters: `blog.corsego.com?query=test` → `blog.superails.com?query=test`

## Example

- `blog.corsego.com/about` → `blog.superails.com/about`
- `blog.corsego.com/posts/123` → `blog.superails.com/posts/123`
- `blog.corsego.com?query=test` → `blog.superails.com?query=test`
