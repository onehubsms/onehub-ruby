# Onehub Ruby Library
```ruby
require 'net/http'
require 'json'

uri = URI('https://api.onehub.co.ke/v1/sms/send')
req = Net::HTTP::Post.new(uri)
req.content_type = 'application/json'
req['x-api-user'] = 'API_USERNAME_HERE'
req['x-api-key'] = 'API_KEY_HERE'

req.body = {
    'phoneNumbers' => '+2547XXXXXXXX,+2547XXXXXXXX',
    'message' => 'Hello Api!',
    'senderId' => 'Onehub'
}.to_json

req_options = {
    use_ssl: uri.scheme == 'https'
}
res = Net::HTTP.start(uri.hostname, uri.port, req_options) do |http|
    http.request(req)
end
```
# Username and API Key
You can get your username and API Key [here](https://dashboard.onehub.co.ke/account/0/user/signup).
# Request Body Parameters
`phoneNumbers` - `[Type: String]` `[Required]` - Phone numbers of the recipients in international format with the plus (+) sign. Multiple numbers should be comma-separated.

`Message` - `[Type: String]` `[Required]` - The message you want to send. Each message is counted as 160 characters long. Messages longer than 160 characters will be billed accordingly.

`Sender ID` - `[Type: String]` `[Required]` - A sender ID serves as a branding for outgoing messages, typically representing your company name. Your users will receive messages with your specified sender ID. You can apply for your sender ID on our [website](https://onehub.co.ke/).
